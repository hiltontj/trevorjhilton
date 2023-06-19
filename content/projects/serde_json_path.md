+++
title = "serde_json_path"

[extra]
link = "https://github.com/hiltontj/serde_json_path"
+++
`serde_json_path` is an open-source implementation of the [IETF JSONPath Specification][ietf_json_path] built for the Rust Programming Language. It is meant to be used alongside the [`serde_json`][serde_json] Rust crate to parse and extract information from arbitrary JSON data.

JSONPath provides a concise, but powerful query syntax that can be used to select nodes within a JSON object. Combined with Rust's rich and reliable type system, it can be a valuable tool when working with JSON.

You can add `serde_json_path` to your Rust applications from the [crates.io][crates] page, find out more about how to use it from the [crate documentation][docs], and even play around with it in the [sandbox][sandbox].

[ietf_json_path]: https://datatracker.ietf.org/wg/jsonpath/about/
[serde_json]: https://docs.rs/serde_json/latest/serde_json/
[crates]: https://crates.io/crates/serde_json_path
[docs]: https://docs.rs/serde_json_path/latest/serde_json_path/
[sandbox]: https://serdejsonpath.live/