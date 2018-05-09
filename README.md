Terraform Provider [![wercker status](https://app.wercker.com/status/a660ce322102e732b9c53a690f6c7078/s/master "wercker status")](https://app.wercker.com/project/byKey/a660ce322102e732b9c53a690f6c7078)
==================

- Website: https://www.terraform.io
- Mailing list: [Google Groups](http://groups.google.com/group/terraform-tool)

<img src="https://cdn.rawgit.com/hashicorp/terraform-website/master/content/source/assets/images/logo-hashicorp.svg" width="600px">

Requirements
------------

-	[Terraform](https://www.terraform.io/downloads.html) 0.11.x
-	[Go](https://golang.org/doc/install) 1.10 (to build the provider plugin)

Building The Provider
---------------------

Clone repository to: `$GOPATH/src/github.com/yieldr/terraform-provider-auth0`

```sh
$ mkdir -p $GOPATH/src/github.com/yieldr; cd $GOPATH/src/github.com/yieldr
$ git clone git@github.com:yieldr/terraform-provider-auth0
```

Enter the provider directory and build the provider

```sh
$ cd $GOPATH/src/github.com/yieldr/terraform-provider-auth0
$ make build
```

Using the provider
----------------------

To use the provider define the `auth0` provider in your `*.tf` file.

```
provider "auth0" {
  "domain" = "<doman>"
  "client_id" = "<client-id>"
  "client_secret" = "<client-secret>"
}
```

These variables can also be accessed via the `AUTH0_DOMAIN`, `AUTH0_CLIENT_ID` and `AUTH0_CLIENT_SECRET` environment variables respectively.

Examples of resources can be found in the [examples directory](examples/). The currently supported Auth0 resources are described in the following table.

| Resource      | Supported |
| ------------- |:---------:|
| [Clients (Applications)](https://auth0.com/docs/api/management/v2#!/Clients/get_clients) | Yes |
| [Client Grants](https://auth0.com/docs/api/management/v2#!/Client_Grants/get_client_grants) | Yes |
| [Connections](https://auth0.com/docs/api/management/v2#!/Connections/get_connections) | No |
| [Custom Domains](https://auth0.com/docs/api/management/v2#!/Custom_Domains/get_custom_domains) | No |
| [Device Credentials](https://auth0.com/docs/api/management/v2#!/Device_Credentials/get_device_credentials) | No |
| [Grants](https://auth0.com/docs/api/management/v2#!/Grants/get_grants) | No |
| [Resource Servers (APIs)](https://auth0.com/docs/api/management/v2#!/Resource_Servers/get_resource_servers) | Yes |
| [Rules](https://auth0.com/docs/api/management/v2#!/Rules/get_rules) | No |
| [Rules Configs](https://auth0.com/docs/api/management/v2#!/Rules_Configs/get_rules_configs) | No |
| [User Blocks](https://auth0.com/docs/api/management/v2#!/User_Blocks/get_user_blocks) | No |
| [Users](https://auth0.com/docs/api/management/v2#!/Users/get_users) | No |
| [Users By Email](https://auth0.com/docs/api/management/v2#!/Users_By_Email/get_users_by_email) | No |
| [Blacklists](https://auth0.com/docs/api/management/v2#!/Blacklists/get_tokens) | No |
| [Email Templates](https://auth0.com/docs/api/management/v2#!/Email_Templates/get_email_templates_by_templateName) | No |
| [Emails](https://auth0.com/docs/api/management/v2#!/Emails/get_provider) | No |
| [Guardian](https://auth0.com/docs/api/management/v2#!/Guardian/get_factors) | No |
| [Jobs](https://auth0.com/docs/api/management/v2#!/Jobs/get_jobs_by_id) | No |
| [Tenants](https://auth0.com/docs/api/management/v2#!/Tenants/get_settings) | No |
| [Tickets](https://auth0.com/docs/api/management/v2#!/Tickets/post_email_verification) | No |

If you need resources that are not available yet, please consider helping the project by contributing.

Developing the Provider
---------------------------

If you wish to work on the provider, you'll first need [Go](http://www.golang.org) installed on your machine (version 1.10+ is *required*). You'll also need to correctly setup a [GOPATH](http://golang.org/doc/code.html#GOPATH), as well as adding `$GOPATH/bin` to your `$PATH`.

On how to develop custom terraform providers, read the [official guide](https://www.terraform.io/docs/extend/writing-custom-providers.html).

To compile the provider, run `make install`. This will build the provider and install the provider binary in the `$GOPATH/bin` directory.

```sh
$ make install
...
$ $GOPATH/bin/terraform-provider-auth0
...
```

In order to test the provider, you can simply run `make test`.

```sh
$ make test
```

In order to run the full suite of Acceptance tests, run `make testacc`.

*Note:* Acceptance tests create real resources, and often cost money to run.

```sh
$ make testacc
```
