+++
title = "serde_json_path"
weight = 0

[extra]
github = "https://github.com/hiltontj/serde_json_path"
docs = "https://docs.rs/serde_json_path/latest/serde_json_path"
package = "https://crates.io/crates/serde_json_path"
+++
`serde_json_path` is an open-source implementation of the [IETF JSONPath Specification][ietf_json_path] built for the Rust Programming Language. It is meant to be used alongside the [`serde_json`][serde_json] Rust package to query and extract information from arbitrary JSON data.

<!-- more -->

JSONPath provides a concise and powerful query syntax that can be used to select nodes within a JSON object. Combined with Rust's rich and reliable type system, JSONPath can be a valuable tool to have when working with JSON in your data pipelines, web services, and more.

You can add `serde_json_path` to your Rust application from the [crates.io][crates] page, find out more about how to use it from the [crate documentation][docs], or try your hand at a few JSONPath queries in the [sandbox][sandbox].

[ietf_json_path]: https://datatracker.ietf.org/wg/jsonpath/about/
[serde_json]: https://docs.rs/serde_json/latest/serde_json/
[crates]: https://crates.io/crates/serde_json_path
[docs]: https://docs.rs/serde_json_path/latest/serde_json_path/
[sandbox]: https://serdejsonpath.live/