# Azure client library test utilities

The types and functions in this crate help test client libraries built on `azure_core`.

## Client methods

To test client methods using our [Test Proxy], you can attribute both synchronous and asynchronous (recommend) tests
using the `#[recorded::test]` attribute:

```rust
use azure_core_test::{recorded, TestContext};
use azure_core::Result;

#[recorded::test]
async fn get_secret(ctx: TestContext) -> Result<()> {
    todo!()
}
```

The `TestContext` parameter is required unless your test function is attribute as `#[recorded::test(live)]` (live-only),
in which case it is optional. You can name the parameter whatever you want.
The `TestContext` parameter is used to initialize an HTTP client to play back or record tests
and provides other information to test functions that may be useful.

[Test Proxy]: https://github.com/Azure/azure-sdk-tools/blob/main/tools/test-proxy/Azure.Sdk.Tools.TestProxy/README.md
