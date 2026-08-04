**Unreleased**

* Protect the integration URL as secret asset data and stop logging the endpoint; re-save existing assets and rotate integration tokens after upgrading.
* Keep public API credentials off custom integration endpoint requests and require HTTPS integration URLs.
* Validate routing keys before appending them to integration endpoint URLs.
* Reject incident message types that do not match the selected create or update action.
* Handle malformed incident endpoint responses without raising an unhandled exception after delivery.
