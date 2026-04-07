# Changelog

All notable changes to this project will be documented in this file.
The project adheres to [Semantic Versioning](https://semver.org).

## **1.1.0** / 2026-04-07

### Added
- **Tests**: Integrated a comprehensive test suite. Currently passing 40 out of 40 tests to ensure middleware stability.

### Changed
- **Origin Validation**: Strict origin checking for string-based `origin` option. Previously any string was accepted; now the middleware validates that the request origin matches the configured origin (or allows `'*'`), otherwise throws 403.
- **Error Handling**: Refactored the header merging logic during exceptions. The middleware now:
  - Removes existing `Vary`/`vary` headers from the error object before injecting a merged `Origin` value to prevent duplicates and casing issues.
  - No longer uses `instanceof HttpError` checks, simplifying error handling across different error types.
- **Header Consistency**: Improved how `err.headers` are constructed to ensure CORS headers are reliably attached to all thrown objects, regardless of their origin.

### Removed
- **`http-errors` dependency**: The middleware no longer relies on runtime `HttpError` checks, using only the type import. This makes it more lightweight and compatible with various error-throwing patterns.

## **1.0.0** / 2026-04-05

### Info
- Initial release.
