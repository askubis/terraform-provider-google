---
# ----------------------------------------------------------------------------
#
#     ***     AUTO GENERATED CODE    ***    Type: MMv1     ***
#
# ----------------------------------------------------------------------------
#
#     This file is automatically generated by Magic Modules and manual
#     changes will be clobbered when the file is regenerated.
#
#     Please read more about how to change this file in
#     .github/CONTRIBUTING.md.
#
# ----------------------------------------------------------------------------
subcategory: "Network services"
description: |-
  Gateway represents the configuration for a proxy, typically a load balancer.
---

# google\_network\_services\_gateway

Gateway represents the configuration for a proxy, typically a load balancer.
It captures the ip:port over which the services are exposed by the proxy,
along with any policy configurations. Routes have reference to to Gateways
to dictate how requests should be routed by this Gateway.

~> **Warning:** This resource is in beta, and should be used with the terraform-provider-google-beta provider.
See [Provider Versions](https://terraform.io/docs/providers/google/guides/provider_versions.html) for more details on beta resources.

To get more information about Gateway, see:

* [API documentation](https://cloud.google.com/traffic-director/docs/reference/network-services/rest/v1beta1/projects.locations.gateways)

<div class = "oics-button" style="float: right; margin: 0 0 -15px">
  <a href="https://console.cloud.google.com/cloudshell/open?cloudshell_git_repo=https%3A%2F%2Fgithub.com%2Fterraform-google-modules%2Fdocs-examples.git&cloudshell_working_dir=network_services_gateway_basic&cloudshell_image=gcr.io%2Fgraphite-cloud-shell-images%2Fterraform%3Alatest&open_in_editor=main.tf&cloudshell_print=.%2Fmotd&cloudshell_tutorial=.%2Ftutorial.md" target="_blank">
    <img alt="Open in Cloud Shell" src="//gstatic.com/cloudssh/images/open-btn.svg" style="max-height: 44px; margin: 32px auto; max-width: 100%;">
  </a>
</div>
## Example Usage - Network Services Gateway Basic


```hcl
resource "google_network_services_gateway" "default" {
  provider = google-beta
  name     = "my-gateway"
  scope    = "default-scope-basic"
  type     = "OPEN_MESH"
  ports    = [443]
}
```
<div class = "oics-button" style="float: right; margin: 0 0 -15px">
  <a href="https://console.cloud.google.com/cloudshell/open?cloudshell_git_repo=https%3A%2F%2Fgithub.com%2Fterraform-google-modules%2Fdocs-examples.git&cloudshell_working_dir=network_services_gateway_advanced&cloudshell_image=gcr.io%2Fgraphite-cloud-shell-images%2Fterraform%3Alatest&open_in_editor=main.tf&cloudshell_print=.%2Fmotd&cloudshell_tutorial=.%2Ftutorial.md" target="_blank">
    <img alt="Open in Cloud Shell" src="//gstatic.com/cloudssh/images/open-btn.svg" style="max-height: 44px; margin: 32px auto; max-width: 100%;">
  </a>
</div>
## Example Usage - Network Services Gateway Advanced


```hcl
resource "google_network_services_gateway" "default" {
  provider    = google-beta
  name        = "my-gateway"
  labels      = {
    foo = "bar"
  }
  description = "my description"
  type        = "OPEN_MESH"
  ports       = [443]
  scope       = "default-scope-advance"
}
```

## Argument Reference

The following arguments are supported:


* `type` -
  (Required)
  Immutable. The type of the customer-managed gateway. Possible values are: * OPEN_MESH * SECURE_WEB_GATEWAY.
  Possible values are `TYPE_UNSPECIFIED`, `OPEN_MESH`, and `SECURE_WEB_GATEWAY`.

* `ports` -
  (Required)
  One or more port numbers (1-65535), on which the Gateway will receive traffic.
  The proxy binds to the specified ports. Gateways of type 'SECURE_WEB_GATEWAY' are 
  limited to 1 port. Gateways of type 'OPEN_MESH' listen on 0.0.0.0 and support multiple ports.

* `scope` -
  (Required)
  Immutable. Scope determines how configuration across multiple Gateway instances are merged.
  The configuration for multiple Gateway instances with the same scope will be merged as presented as
  a single coniguration to the proxy/load balancer. 
  Max length 64 characters. Scope should start with a letter and can only have letters, numbers, hyphens.

* `name` -
  (Required)
  Short name of the Gateway resource to be created.


- - -


* `labels` -
  (Optional)
  Set of label tags associated with the Gateway resource.

* `description` -
  (Optional)
  A free-text description of the resource. Max length 1024 characters.

* `server_tls_policy` -
  (Optional)
  A fully-qualified ServerTLSPolicy URL reference. Specifies how TLS traffic is terminated.
  If empty, TLS termination is disabled.

* `location` -
  (Optional)
  The location of the gateway.
  The default value is `global`.

* `project` - (Optional) The ID of the project in which the resource belongs.
    If it is not provided, the provider project is used.


## Attributes Reference

In addition to the arguments listed above, the following computed attributes are exported:

* `id` - an identifier for the resource with format `projects/{{project}}/locations/{{location}}/gateways/{{name}}`

* `self_link` -
  Server-defined URL of this resource.

* `create_time` -
  Time the AccessPolicy was created in UTC.

* `update_time` -
  Time the AccessPolicy was updated in UTC.


## Timeouts

This resource provides the following
[Timeouts](https://developer.hashicorp.com/terraform/plugin/sdkv2/resources/retries-and-customizable-timeouts) configuration options:

- `create` - Default is 30 minutes.
- `update` - Default is 30 minutes.
- `delete` - Default is 30 minutes.

## Import


Gateway can be imported using any of these accepted formats:

```
$ terraform import google_network_services_gateway.default projects/{{project}}/locations/{{location}}/gateways/{{name}}
$ terraform import google_network_services_gateway.default {{project}}/{{location}}/{{name}}
$ terraform import google_network_services_gateway.default {{location}}/{{name}}
```

## User Project Overrides

This resource supports [User Project Overrides](https://registry.terraform.io/providers/hashicorp/google/latest/docs/guides/provider_reference#user_project_override).