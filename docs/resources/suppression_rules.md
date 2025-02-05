---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "squadcast_suppression_rules Resource - terraform-provider-squadcast"
subcategory: ""
description: |-
  Suppression rules https://support.squadcast.com/docs/alert-suppression can help you avoid alert fatigue by suppressing notifications for non-actionable alerts.Squadcast will suppress the incidents that match any of the Suppression Rules you create for your Services. These incidents will go into the Suppressed state and you will not get any notifications for them
---

# squadcast_suppression_rules (Resource)

[Suppression rules](https://support.squadcast.com/docs/alert-suppression) can help you avoid alert fatigue by suppressing notifications for non-actionable alerts.Squadcast will suppress the incidents that match any of the Suppression Rules you create for your Services. These incidents will go into the Suppressed state and you will not get any notifications for them

## Example Usage

```terraform
data "squadcast_team" "example_resource_name" {
  name = "exammple team name"
}

data "squadcast_service" "example_resource_name" {
  name = "example service name"
}

resource "squadcast_suppression_rules" "example_resource_name" {
  team_id    = data.squadcast_team.example_resource_name.id
  service_id = data.squadcast_service.example_resource_name.id

  rules {
    is_basic    = false
    description = "not basic"
    expression  = "payload[\"event_id\"] == 40"
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
- `description` (String) description.
- `expression` (String) The expression which needs to be evaluated to be true for this rule to apply.

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
terraform import squadcast_suppression_rules.test 62d2fe23a57381088224d726:62da76c088f407f9ca756ca5
```
