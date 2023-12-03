+++
title = "IETF JSONPath for The Rust Programming Language"
author = "Trevor Hilton"
description = "An introduction to the serde_json_path crate, for using IETF JSONPath in your Rust programs."

[extra]
+++
Earlier this year, I published the [`serde_json_path` crate][sjp-crates], a library that allows you to leverage IETF JSONPath in your Rust programs. This article provides an introduction to `serde_json_path` and some of its derivatives.

<!-- more -->

## What is IETF JSONPath?

JSONPath, a tool for querying and extracting nodes from JSON objects, was originally described by [Setfan Gössner in 2007][gossner]. Gössner's articles have been the basis for JSONPath's widespread adoption and implementation. Most existing implementations of JSONPath, including those available to the Rust Programming Language, use them as a framework.

Recently, the IETF formed a [working group to standardize JSONPath][ietf-wg]. Led by the same Stefan Gössner, as well as Glyn Normington and Carsten Bormann, the group has produced an extensive, clear, and precise standard for JSONPath. You can read the document in various formats [here][ietf-base]. It will likely be published as an RFC [by early 2024][glyn-blog].

## The `serde_json_path` crate

I generally use the [`serde_json` crate][serde-json-crates] to work with JSON in Rust. Some time ago, I had a use for JSONPath. A keyword search for ["jsonpath" on crates.io][crates-jsonpath] reveals that there are several JSONPath implementations available to Rust programmers; however, I did not feel the API or documentation of these crates was up to the standard of quality set by the Rust ecosystem.

I published the [`serde_json_path` crate][sjp-crates] to provide Rust developers with a JSONPath implementation that is:

- fully compliant with the IETF JSONPath specification,
- provides a concise and idiomatic API that is thoroughly documented, and
- plays nice with `serde_json`.

Have a look at [the crate documentation][sjp-docs] for a broad overview of JSONPath capability and how to use `serde_json_path`. I also encourage readers to check out the IETF standard to understand the nitty-gritty details of what they can do with their JSONPath queries.

### A note on compliance

Although not officially affiliated with the IETF working group, a [compliance test suite (CTS)][cts] is being actively developed to establish compliance of JSONPath implementations with the IETF standard. `serde_json_path` is kept up-to-date with the CTS to ensure that it covers all the corners and edge cases of the specification.

## WASM and JSONPath Sandbox

You can try out IETF JSONPath in [the sandbox environment][sjp-live]. The sandbox parses and executes JSONPath queries entirely in the browser by utilizing the [`serde-json-path` NPM package][sjp-npm]– which takes `serde_json_path` and compiles it to WASM.

[gossner]: https://goessner.net/articles/JsonPath/
[ietf-wg]: https://datatracker.ietf.org/wg/jsonpath/about/
[ietf-base]: https://datatracker.ietf.org/doc/draft-ietf-jsonpath-base/
[glyn-blog]: https://underlap.org/jsonpath-rfc-nearing-publication
[sjp-crates]: https://crates.io/crates/serde_json_path
[sjp-docs]: https://docs.rs/serde_json_path/latest/serde_json_path
[sjp-live]: https://serdejsonpath.live
[sjp-npm]: https://www.npmjs.com/package/serde-json-path
[serde-json-crates]: https://crates.io/crates/serde_json
[crates-jsonpath]: https://crates.io/keywords/jsonpath
[cts]: https://github.com/jsonpath-standard/jsonpath-compliance-test-suite