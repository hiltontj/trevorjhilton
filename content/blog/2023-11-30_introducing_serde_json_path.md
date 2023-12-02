+++
title = "IETF JSONPath for the Rust Programming Language"
author = "Trevor Hilton"
description = "An introduction to the serde_json_path Rust crate."

[extra]
+++
This article gives an introduction to the [`serde_json_path` crate][sjp-crates], a library that allows you to leverage IETF JSONPath in your Rust programs.

<!-- more -->

- [What is JSONPath?](#what-is-jsonpath)
- [When would one use JSONPath?](#when-would-one-use-jsonpath)
- [IETF JSONPath implementation for Rust](#ietf-jsonpath-implementation-for-rust)

### What is JSONPath?

JSONPath is a query syntax that can be used to extract nodes from a JSON object. Originally described by [Stefan Gössner in 2007][gossner], it has been implemented for use with various programming languages and seen widespread adoption. However, without an official specification for JSONPath, existing implementations differ in certain behaviors.

Recently, the IETF formed a [working group][ietf-wg] to standardize JSONPath as an RFC. Led by the same Stefan Gössner, as well as Glyn Normington and Carsten Bormann, this work has been completed and will likely be published as an RFC [by early 2024][glyn-blog]. The specification, which you can find in various formats [here][ietf-base], extensively covers the syntax and usage of JSONPath.

### When would one use JSONPath?

JSONPath is a Swiss army knife in and of itself. I encourage you to read the specification to understand all of its capabilities and decide where and how you might like to use it. Generally speaking, if your application works with JSON, and you need to introduce some dynamic processing or filtering steps, JSONPath is a great tool to have at your disposal.

As an example, say you have an event driven service that broadcasts event information in batches for downstream services to process. Events have an `id`, a `type`, and may have some associated data, depending on the `type`:

```json
{
    "batch": 1,
    "events": [
        { "id": 1, "type": "create", /* more fields */ },
        { "id": 2, "type": "update", /* ... */ },
        { "id": 3, "type": "delete", /* ... */ },
        { "id": 4, "type": "update", /* ... */ }
    ]
}
```

Downstream of this, you have a service that is only interested in events of type `update`. JSONPath makes filtering the data for the downstream service quite trivial.

The query:

```
$.events[? @.type == 'update']
```

would produce the following output:

```json
[
    { "id": 2, "type": "update", /* ... */ },
    { "id": 4, "type": "update", /* ... */ }
]
```

Let's break down what is going on here. Starting with the JSON object root, `$`, first, we extract the event list using `$.events`. Then, we filter that list using a filter selector `[? <expression>]`, which applies `<expression>` to each node, `@`, in the list. In this case, we are comparing each node's `type` field, i.e., `@.type`, to see that it equals the value `"update"`.

If you were only interested in the `id` of each update event, then you could extend this further:

```
$.events[? @.type == 'update'].id
```

to produce the following output:

```json
[2, 4]
```

### IETF JSONPath implementation for Rust

Part of this article's purpose is to introduce `serde_json_path`, the Rust crate that I authored. It is the only JSONPath implementation for Rust that adheres to the IETF standard.

A search on the keyword "jsonpath" in [crates.io][crates-jsonpath] reveals that there are several JSONPath libraries available in the Rust ecosystem.

[gossner]: https://goessner.net/articles/JsonPath/
[ietf-wg]: https://datatracker.ietf.org/wg/jsonpath/about/
[ietf-base]: https://datatracker.ietf.org/doc/draft-ietf-jsonpath-base/
[glyn-blog]: https://underlap.org/jsonpath-rfc-nearing-publication
[sjp-crates]: https://crates.io/crates/serde_json_path
[crates-jsonpath]: https://crates.io/keywords/jsonpath