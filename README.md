[comment]: # "Auto-generated SOAR connector documentation"
# Splunk On\-Call

Publisher: Splunk  
Connector Version: 2\.1\.1  
Product Vendor: VictorOps  
Product Name: VictorOps  
Product Version Supported (regex): "\.\*"  
Minimum Product Version: 5\.1\.0  

Formerly known as VictorOps\. This app implements various investigative actions using VictorOps

[comment]: # " File: README.md"
[comment]: # "Copyright (c) 2018-2022 Splunk Inc."
[comment]: # ""
[comment]: # "Licensed under Apache 2.0 (https://www.apache.org/licenses/LICENSE-2.0.txt)"
[comment]: # ""
[comment]: # ""
To get started with the VictorOps API to integrate with Phantom, log into the VictorOps web portal
and go to Integrations then API. From here you can retrieve your API ID and have the opportunity to
create your API Keys. Note: Only VictorOps admin users can create API Keys. The documentation for
the VictorOps API allows you to try out the different calls in real time. To get started read the
[API Documentation](https://portal.victorops.com/api-docs/#/) .  
  
Phantom integrates with the VictorOps REST Endpoint to trigger, update, or resolve incidents in
VictorOps. To enable this integration in VictorOps, click on Integrations \>\> 3rd Party
Integrations API \>\> REST – Generic. If the REST endpoint integration has not been enabled, click
the blue Enable Integration button to generate your endpoint destination URL.


### Configuration Variables
The below configuration variables are required for this Connector to operate.  These variables are specified when configuring a VictorOps asset in SOAR.

VARIABLE | REQUIRED | TYPE | DESCRIPTION
-------- | -------- | ---- | -----------
**api\_id** |  required  | string | API ID from the VictorOps Portal
**api\_key** |  required  | password | API Key from the VictorOps Portal
**integration\_url** |  optional  | string | Custom REST based Integration URL defined in VictorOps

### Supported Actions  
[test connectivity](#action-test-connectivity) - Validate the asset configuration for connectivity using supplied configuration  
[list teams](#action-list-teams) - Get list of teams configured on VictorOps  
[list users](#action-list-users) - Get list of users configured on VictorOps  
[list incidents](#action-list-incidents) - Get list of incidents on VictorOps  
[create incident](#action-create-incident) - Create incident on VictorOps  
[list oncalls](#action-list-oncalls) - Get all on\-call users/teams on VictorOps  
[list policies](#action-list-policies) - Get list of policies configured on VictorOps  
[list routing](#action-list-routing) - Get list of routing keys and associated teams on VictorOps  
[update incident](#action-update-incident) - Update timeline of existing incident in VictorOps  

## action: 'test connectivity'
Validate the asset configuration for connectivity using supplied configuration

Type: **test**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
No Output  

## action: 'list teams'
Get list of teams configured on VictorOps

Type: **investigate**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.data\.\*\.\_membersUrl | string | 
action\_result\.data\.\*\.\_policiesUrl | string | 
action\_result\.data\.\*\.\_selfUrl | string | 
action\_result\.data\.\*\.isDefaultTeam | boolean | 
action\_result\.data\.\*\.memberCount | numeric | 
action\_result\.data\.\*\.name | string | 
action\_result\.data\.\*\.slug | string | 
action\_result\.data\.\*\.version | numeric | 
action\_result\.summary\.num\_teams | numeric | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'list users'
Get list of users configured on VictorOps

Type: **investigate**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.data\.\*\.\_selfUrl | string | 
action\_result\.data\.\*\.createdAt | string | 
action\_result\.data\.\*\.email | string |  `email` 
action\_result\.data\.\*\.firstName | string |  `email` 
action\_result\.data\.\*\.lastName | string | 
action\_result\.data\.\*\.passwordLastUpdated | string | 
action\_result\.data\.\*\.username | string |  `user name` 
action\_result\.data\.\*\.verified | boolean | 
action\_result\.summary\.num\_users | numeric | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'list incidents'
Get list of incidents on VictorOps

Type: **investigate**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.data\.\*\.alertCount | numeric | 
action\_result\.data\.\*\.currentPhase | string | 
action\_result\.data\.\*\.entityDisplayName | string | 
action\_result\.data\.\*\.entityId | string |  `victorops id` 
action\_result\.data\.\*\.entityState | string | 
action\_result\.data\.\*\.entityType | string | 
action\_result\.data\.\*\.host | string | 
action\_result\.data\.\*\.incidentNumber | string | 
action\_result\.data\.\*\.lastAlertId | string | 
action\_result\.data\.\*\.lastAlertTime | string | 
action\_result\.data\.\*\.pagedPolicies\.\*\.policy\.name | string | 
action\_result\.data\.\*\.pagedPolicies\.\*\.policy\.slug | string | 
action\_result\.data\.\*\.pagedPolicies\.\*\.team\.name | string | 
action\_result\.data\.\*\.pagedPolicies\.\*\.team\.slug | string | 
action\_result\.data\.\*\.pagedTeams | string | 
action\_result\.data\.\*\.routingKey | string | 
action\_result\.data\.\*\.service | string | 
action\_result\.data\.\*\.startTime | string | 
action\_result\.data\.\*\.transitions\.\*\.at | string | 
action\_result\.data\.\*\.transitions\.\*\.by | string | 
action\_result\.data\.\*\.transitions\.\*\.manually | boolean | 
action\_result\.data\.\*\.transitions\.\*\.name | string | 
action\_result\.summary\.num\_incidents | numeric | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'create incident'
Create incident on VictorOps

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**routing\_key** |  optional  | Name of Routing key defined in VictorOps\. If left blank, default route will be used | string | 
**message\_type** |  required  | Behavior of the alert\. CRITICAL\: Triggers an incident, WARNING\: May trigger an incident, depending on your settings | string | 
**entity\_id** |  optional  | ID of the Incident\. This field is the identity of the incident and must remain the same throughout the life\-cycle of an incident\. If no entity\_id is included, VictorOps will generate a random string | string |  `victorops id` 
**entity\_display\_name** |  optional  | Display Name in the UI and Notifications\. This field allows you to give custom, human\-friendly, summary of your incidents without affecting the life\-cycle workflow | string |  `victorops display name` 
**state\_message** |  optional  | Verbose message field\. This field has a high character limit and is intended for a long, verbose, explanation of the problem\. This field will be included in notifications \(full content in email, truncated version in push/phone/SMS notifications\) Any URL links included in this field will be rendered as clickable links in email notifications | string | 
**state\_start\_time** |  optional  | Time this issue began \[Number\] \(Linux/Unix time\)\. The time this entity entered its current state \(seconds since epoch\)\. Defaults to the time alert is received | numeric | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.entity\_display\_name | string |  `victorops display name` 
action\_result\.parameter\.entity\_id | string |  `victorops id` 
action\_result\.parameter\.message\_type | string | 
action\_result\.parameter\.routing\_key | string | 
action\_result\.parameter\.state\_message | string | 
action\_result\.parameter\.state\_start\_time | numeric | 
action\_result\.data\.\*\.entity\_id | string |  `victorops id` 
action\_result\.data\.\*\.result | string | 
action\_result\.summary\.entity\_id | string |  `victorops id` 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'list oncalls'
Get all on\-call users/teams on VictorOps

Type: **investigate**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.data\.\*\.oncallNow\.\*\.escalationPolicy\.name | string | 
action\_result\.data\.\*\.oncallNow\.\*\.escalationPolicy\.slug | string | 
action\_result\.data\.\*\.oncallNow\.\*\.users\.\*\.onCalluser\.username | string |  `user name` 
action\_result\.data\.\*\.team\.name | string | 
action\_result\.data\.\*\.team\.slug | string | 
action\_result\.summary\.num\_teams\_oncall | numeric | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'list policies'
Get list of policies configured on VictorOps

Type: **investigate**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.data\.\*\.policy\.name | string | 
action\_result\.data\.\*\.policy\.slug | string | 
action\_result\.data\.\*\.team\.name | string | 
action\_result\.data\.\*\.team\.slug | string | 
action\_result\.summary\.num\_policies | numeric | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'list routing'
Get list of routing keys and associated teams on VictorOps

Type: **investigate**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.data\.\*\.isDefault | boolean | 
action\_result\.data\.\*\.routingKey | string | 
action\_result\.data\.\*\.targets\.\*\.\_teamUrl | string | 
action\_result\.data\.\*\.targets\.\*\.policyName | string | 
action\_result\.data\.\*\.targets\.\*\.policySlug | string | 
action\_result\.summary\.num\_routing\_keys | numeric | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'update incident'
Update timeline of existing incident in VictorOps

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**routing\_key** |  optional  | Name of Routing key defined in VictorOps\. If left blank, default route will be used | string | 
**message\_type** |  required  | Behavior of the alert\. INFO\: Creates a timeline event but does not trigger an incident\. RECOVERY\: Resolves an incident | string | 
**entity\_id** |  optional  | The entity\_id of an existing incident\. If not included, an update will be posted on timeline | string |  `victorops id` 
**entity\_display\_name** |  optional  | Display Name in the UI and Notifications\. This field allows you to give custom, human\-friendly, summary of your incidents without affecting the life\-cycle workflow | string |  `victorops display name` 
**state\_message** |  optional  | Verbose message field\. This field has a high character limit and is intended for a long, verbose, explanation of the problem\. This field will be included in notifications \(full content in email, truncated version in push/phone/SMS notifications\) Any URL links included in this field will be rendered as clickable links in email notifications | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.entity\_display\_name | string |  `victorops display name` 
action\_result\.parameter\.entity\_id | string |  `victorops id` 
action\_result\.parameter\.message\_type | string | 
action\_result\.parameter\.routing\_key | string | 
action\_result\.parameter\.state\_message | string | 
action\_result\.data\.\*\.entity\_id | string |  `victorops id` 
action\_result\.data\.\*\.result | string | 
action\_result\.summary\.entity\_id | string |  `victorops id` 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric | 