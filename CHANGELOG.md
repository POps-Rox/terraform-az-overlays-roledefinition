# Changelog

## [2.0.0] - 2026-05-11

### Changed (BREAKING)

- Upgraded `hashicorp/azurerm` provider constraint from `~> 3.116` to `~> 4.20`.
- Raised minimum Terraform CLI version from `>= 1.9` to `>= 1.10`.

### Added

- New `azure/azapi ~> 2.0` and `POps-Rox/azutils ~> 1.0` (`popsrox`) provider
  declarations in `versions.tf` (root + example) for fleet alignment.
- Comment in the example `provider "azurerm"` block noting that
  `subscription_id` is provided by the consumer via the `ARM_SUBSCRIPTION_ID`
  environment variable (required by azurerm 4.x).

### Notes

- Module manages only `azurerm_role_definition` resources. The Phase 1 KV-4
  codemod (`azurerm_role_assignment.principal_type`) does **not** apply here —
  this module does not create role assignments. Consumers that wrap this
  module with their own `azurerm_role_assignment` resources should follow
  KV-4 in their own code.
- No mechanical attribute renames (`enable_*`, `allow_blob_public_access`,
  retention_policy, subnet endpoint policies, `skip_provider_registration`)
  were required.
- `terraform validate` passes on both the root module and `examples/basic`
  with the new constraints — no transitive failures because the example
  sources the module locally (`../..`) rather than from a sibling overlay
  repo.

# v1.0.0 - <date>

Added
- Add Something you added
