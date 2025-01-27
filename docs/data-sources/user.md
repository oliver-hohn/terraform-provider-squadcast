---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "squadcast_user Data Source - terraform-provider-squadcast"
subcategory: ""
description: |-
  Use this data source to get information about a specific user that you can use for other Squadcast resources.
---

# squadcast_user (Data Source)

Use this data source to get information about a specific user that you can use for other Squadcast resources.

## Example Usage

```terraform
data "squadcast_user" "test" {
  email = squadcast_user.test.email
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `email` (String) User email.

### Read-Only

- `abilities` (List of String) Denotes the Permissions / abilities of the user.
- `first_name` (String) User first name.
- `id` (String) User id.
- `is_email_verified` (Boolean) Denotes if the user has verified their email or not.
- `is_override_dnd_enabled` (Boolean) Deprecated, this can be ignored.
- `is_phone_verified` (Boolean) Denotes if the user has verified their phone number or not.
- `last_name` (String) User last name.
- `name` (String) User name, automatically computed from first name and last name.
- `notification_rules` (List of Object) User Personal Notification Rules. (see [below for nested schema](#nestedatt--notification_rules))
- `oncall_reminder_rules` (List of Object) User's personal on-call reminder notification rules. (see [below for nested schema](#nestedatt--oncall_reminder_rules))
- `phone` (String) User phone number.
- `role` (String) User role.
- `time_zone` (String) User time_zone.

<a id="nestedatt--notification_rules"></a>
### Nested Schema for `notification_rules`

Read-Only:

- `delay_minutes` (Number)
- `type` (String)


<a id="nestedatt--oncall_reminder_rules"></a>
### Nested Schema for `oncall_reminder_rules`

Read-Only:

- `delay_minutes` (Number)
- `type` (String)


