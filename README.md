temp-env
========

Set environment variables temporarily.

This crate is useful for testing with different environment variables that should not interfere.

This code started as a small test helper written by [@fabian-braun] and [@nbaztec] and published by [@fabian-braun]
on [StackOverflow]. [@vmx] found it useful and took the time to make it a proper crate.

Example
-------

```rust
temp_env::with_var("MY_ENV_VAR", Some("production"), || {
    // Run some code where `MY_ENV_VAR` set to `"production"`.
});


temp_env::with_vars(
    vec![
        ("FIRST_VAR", Some("Hello")),
        ("SECOND_VAR", Some("World!")),
    ],
    || {
        // Run some code where `FIRST_VAR` is set to `"Hello"` and `SECOND_VAR` is set to
        // `"World!"`.
    }
);

temp_env::with_vars(
    vec![
        ("FIRST_VAR", Some("Hello")),
        ("SECOND_VAR", None),
    ],
    || {
        // Run some code where `FIRST_VAR` is set to `"Hello"` and `SECOND_VAR` is unset (even if
        // it was set before)
    }
);
```


License
-------

This project is licensed under either of

 * Apache License, Version 2.0, ([LICENSE-APACHE]) or https://www.apache.org/licenses/LICENSE-2.0)
 * MIT license ([LICENSE-MIT] or https://opensource.org/licenses/MIT)

at your option.


[StackOverflow]: https://stackoverflow.com/questions/35858323/how-can-i-test-rust-methods-that-depend-on-environment-variables/67433684#67433684
[@fabian-braun]: https://github.com/fabian-braun
[@nbaztec]: https://github.com/nbaztec
[@vmx]: https://github.com/vmx
[LICENSE-APACHE]: LICENSE-APACHE
[LICENSE-MIT]: LICENSE-MIT
