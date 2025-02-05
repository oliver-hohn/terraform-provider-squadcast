---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "squadcast_deduplication_rules Resource - terraform-provider-squadcast"
subcategory: ""
description: |-
  Deduplication rules https://support.squadcast.com/docs/de-duplication-rules can help you reduce alert noise by organising and grouping alerts. This also provides easy access to similar alerts when needed. When these rules evaluate to true for an incoming incident, alerts will get deduplicated.
---

# squadcast_deduplication_rules (Resource)

[Deduplication rules](https://support.squadcast.com/docs/de-duplication-rules) can help you reduce alert noise by organising and grouping alerts. This also provides easy access to similar alerts when needed. When these rules evaluate to true for an incoming incident, alerts will get deduplicated.

## Example Usage

```terraform
data "squadcast_team" "example_resource_name" {
  name = "example team name"
}

data "squadcast_service" "example_resource_name" {
  name = "example service name"
}

resource "squadcast_deduplication_rules" "example_resource_name" {
  team_id    = data.squadcast_team.example_resource_name.id
  service_id = data.squadcast_service.example_resource_name.id

  rules {
    is_basic    = false
    description = "not basic"
    expression  = "payload[\"event_id\"] == 40"
  }

  rules {
    is_basic    = true
    description = "basic"

    basic_expressions {
      lhs = "payload[\"foo\"]"
      op  = "is"
      rhs = "bar"
    }
  }
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `rules` (Block List, Min: 1) (see [below for nested schema](#nestedblock--rules))
- `service_id` (String) Service id.
- `team_id` (String) Team id.

### Read-Only

- `id` (String) id.

<a id="nestedblock--rules"></a>
### Nested Schema for `rules`

Required:

- `is_basic` (Boolean) is_basic will be true when users use the drop down selectors which will have lhs, op & rhs value, whereas it will be false when they use the advanced mode and it would have the expression for it's value

Optional:

- `basic_expressions` (Block List) The basic expression which needs to be evaluated to be true for this rule to apply. (see [below for nested schema](#nestedblock--rules--basic_expressions))
- `dependency_deduplication` (Boolean) Denotes if dependent services should also be deduplicated
- `description` (String) description.
- `expression` (String) The expression which needs to be evaluated to be true for this rule to apply.
- `time_unit` (String) time unit (mins or hours)
- `time_window` (Number) integer for time_unit

<a id="nestedblock--rules--basic_expressions"></a>
### Nested Schema for `rules.basic_expressions`

Required:

- `lhs` (String) left hand side dropdown value
- `op` (String) operator
- `rhs` (String) right hand side value

## Import

Import is supported using the following syntax:

```shell
# teamID:serviceID
# Use 'Get All Teams' and 'Get All Services' APIs to get the id of the team and service respectively 
terraform import squadcast_deduplication_rules.test_resource_name 62d2fe23a57381088224d726:62da76c088f407f9ca756ca5
```
