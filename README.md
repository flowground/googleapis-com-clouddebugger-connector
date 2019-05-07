# ![LOGO](logo.png) Stackdriver Debugger **flow**ground Connector

## Description

A generated **flow**ground connector for the Stackdriver Debugger API (version v2).

Generated from: https://api.apis.guru/v2/specs/googleapis.com/clouddebugger/v2/swagger.json<br/>
Generated at: 2019-05-07T17:41:18+03:00

## API Description

Examines the call stack and variables of a running application without stopping or slowing it down.


## Authorization

Supported authorization schemes:
- OAuth2

For OAuth 2.0 you need to specify OAuth Client credentials as environment variables in the connector repository:
* `OAUTH_CLIENT_ID` - your OAuth client id
* `OAUTH_CLIENT_SECRET` - your OAuth client secret

## Actions

### Registers the debuggee with the controller service.<br/>
> <br/>
> All agents attached to the same application must call this method with<br/>
> exactly the same request content to get back the same stable `debuggee_id`.<br/>
> Agents should call this method again whenever `google.rpc.Code.NOT_FOUND`<br/>
> is returned from any controller method.<br/>
> <br/>
> This protocol allows the controller service to disable debuggees, recover<br/>
> from data loss, or change the `debuggee_id` format. Agents must handle<br/>
> `debuggee_id` value changing upon re-registration.

*Tags:* `controller`

#### Input Parameters
* `$.xgafv` - _optional_ - V1 error format.
    Possible values: 1, 2.
* `access_token` - _optional_ - OAuth access token.
* `alt` - _optional_ - Data format for response.
    Possible values: json, media, proto.
* `callback` - _optional_ - JSONP
* `fields` - _optional_ - Selector specifying which fields to include in a partial response.
* `key` - _optional_ - API key. Your API key identifies your project and provides you with API access, quota, and reports. Required unless you provide an OAuth 2.0 token.
* `oauth_token` - _optional_ - OAuth 2.0 token for the current user.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters.
* `uploadType` - _optional_ - Legacy upload protocol for media (e.g. "media", "multipart").
* `upload_protocol` - _optional_ - Upload protocol for media (e.g. "raw", "multipart").

### Returns the list of all active breakpoints for the debuggee.<br/>
> <br/>
> The breakpoint specification (`location`, `condition`, and `expressions`<br/>
> fields) is semantically immutable, although the field values may<br/>
> change. For example, an agent may update the location line number<br/>
> to reflect the actual line where the breakpoint was set, but this<br/>
> doesn't change the breakpoint semantics.<br/>
> <br/>
> This means that an agent does not need to check if a breakpoint has changed<br/>
> when it encounters the same breakpoint on a successive call.<br/>
> Moreover, an agent should remember the breakpoints that are completed<br/>
> until the controller removes them from the active list to avoid<br/>
> setting those breakpoints again.

*Tags:* `controller`

#### Input Parameters
* `debuggeeId` - _required_ - Identifies the debuggee.
* `successOnTimeout` - _optional_ - If set to `true` (recommended), returns `google.rpc.Code.OK` status and
sets the `wait_expired` response field to `true` when the server-selected
timeout has expired.

If set to `false` (deprecated), returns `google.rpc.Code.ABORTED` status
when the server-selected timeout has expired.
* `waitToken` - _optional_ - A token that, if specified, blocks the method call until the list
of active breakpoints has changed, or a server-selected timeout has
expired. The value should be set from the `next_wait_token` field in
the last response. The initial value should be set to `"init"`.
* `callback` - _optional_ - JSONP
* `fields` - _optional_ - Selector specifying which fields to include in a partial response.
* `key` - _optional_ - API key. Your API key identifies your project and provides you with API access, quota, and reports. Required unless you provide an OAuth 2.0 token.
* `oauth_token` - _optional_ - OAuth 2.0 token for the current user.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters.
* `uploadType` - _optional_ - Legacy upload protocol for media (e.g. "media", "multipart").
* `upload_protocol` - _optional_ - Upload protocol for media (e.g. "raw", "multipart").

### Updates the breakpoint state or mutable fields.<br/>
> The entire Breakpoint message must be sent back to the controller service.<br/>
> <br/>
> Updates to active breakpoint fields are only allowed if the new value<br/>
> does not change the breakpoint specification. Updates to the `location`,<br/>
> `condition` and `expressions` fields should not alter the breakpoint<br/>
> semantics. These may only make changes such as canonicalizing a value<br/>
> or snapping the location to the correct line of code.

*Tags:* `controller`

#### Input Parameters
* `debuggeeId` - _required_ - Identifies the debuggee being debugged.
* `id` - _required_ - Breakpoint identifier, unique in the scope of the debuggee.
* `alt` - _optional_ - Data format for response.
    Possible values: json, media, proto.
* `callback` - _optional_ - JSONP
* `fields` - _optional_ - Selector specifying which fields to include in a partial response.
* `key` - _optional_ - API key. Your API key identifies your project and provides you with API access, quota, and reports. Required unless you provide an OAuth 2.0 token.
* `oauth_token` - _optional_ - OAuth 2.0 token for the current user.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters.
* `uploadType` - _optional_ - Legacy upload protocol for media (e.g. "media", "multipart").
* `upload_protocol` - _optional_ - Upload protocol for media (e.g. "raw", "multipart").

### Lists all the debuggees that the user has access to.

*Tags:* `debugger`

#### Input Parameters
* `clientVersion` - _optional_ - The client version making the call.
Schema: `domain/type/version` (e.g., `google.com/intellij/v1`).
* `includeInactive` - _optional_ - When set to `true`, the result includes all debuggees. Otherwise, the
result includes only debuggees that are active.
* `project` - _optional_ - Project number of a Google Cloud project whose debuggees to list.
* `callback` - _optional_ - JSONP
* `fields` - _optional_ - Selector specifying which fields to include in a partial response.
* `key` - _optional_ - API key. Your API key identifies your project and provides you with API access, quota, and reports. Required unless you provide an OAuth 2.0 token.
* `oauth_token` - _optional_ - OAuth 2.0 token for the current user.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters.
* `uploadType` - _optional_ - Legacy upload protocol for media (e.g. "media", "multipart").
* `upload_protocol` - _optional_ - Upload protocol for media (e.g. "raw", "multipart").

### Lists all breakpoints for the debuggee.

*Tags:* `debugger`

#### Input Parameters
* `action.value` - _optional_ - Only breakpoints with the specified action will pass the filter.
    Possible values: CAPTURE, LOG.
* `clientVersion` - _optional_ - The client version making the call.
Schema: `domain/type/version` (e.g., `google.com/intellij/v1`).
* `debuggeeId` - _required_ - ID of the debuggee whose breakpoints to list.
* `includeAllUsers` - _optional_ - When set to `true`, the response includes the list of breakpoints set by
any user. Otherwise, it includes only breakpoints set by the caller.
* `includeInactive` - _optional_ - When set to `true`, the response includes active and inactive
breakpoints. Otherwise, it includes only active breakpoints.
* `stripResults` - _optional_ - This field is deprecated. The following fields are always stripped out of
the result: `stack_frames`, `evaluated_expressions` and `variable_table`.
* `waitToken` - _optional_ - A wait token that, if specified, blocks the call until the breakpoints
list has changed, or a server selected timeout has expired.  The value
should be set from the last response. The error code
`google.rpc.Code.ABORTED` (RPC) is returned on wait timeout, which
should be called again with the same `wait_token`.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters.
* `uploadType` - _optional_ - Legacy upload protocol for media (e.g. "media", "multipart").
* `upload_protocol` - _optional_ - Upload protocol for media (e.g. "raw", "multipart").

### Sets the breakpoint to the debuggee.

*Tags:* `debugger`

#### Input Parameters
* `clientVersion` - _optional_ - The client version making the call.
Schema: `domain/type/version` (e.g., `google.com/intellij/v1`).
* `debuggeeId` - _required_ - ID of the debuggee where the breakpoint is to be set.
* `alt` - _optional_ - Data format for response.
    Possible values: json, media, proto.
* `callback` - _optional_ - JSONP
* `fields` - _optional_ - Selector specifying which fields to include in a partial response.
* `key` - _optional_ - API key. Your API key identifies your project and provides you with API access, quota, and reports. Required unless you provide an OAuth 2.0 token.
* `oauth_token` - _optional_ - OAuth 2.0 token for the current user.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters.
* `uploadType` - _optional_ - Legacy upload protocol for media (e.g. "media", "multipart").
* `upload_protocol` - _optional_ - Upload protocol for media (e.g. "raw", "multipart").

### Deletes the breakpoint from the debuggee.

*Tags:* `debugger`

#### Input Parameters
* `breakpointId` - _required_ - ID of the breakpoint to delete.
* `clientVersion` - _optional_ - The client version making the call.
Schema: `domain/type/version` (e.g., `google.com/intellij/v1`).
* `debuggeeId` - _required_ - ID of the debuggee whose breakpoint to delete.
* `callback` - _optional_ - JSONP
* `fields` - _optional_ - Selector specifying which fields to include in a partial response.
* `key` - _optional_ - API key. Your API key identifies your project and provides you with API access, quota, and reports. Required unless you provide an OAuth 2.0 token.
* `oauth_token` - _optional_ - OAuth 2.0 token for the current user.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters.
* `uploadType` - _optional_ - Legacy upload protocol for media (e.g. "media", "multipart").
* `upload_protocol` - _optional_ - Upload protocol for media (e.g. "raw", "multipart").

### Gets breakpoint information.

*Tags:* `debugger`

#### Input Parameters
* `breakpointId` - _required_ - ID of the breakpoint to get.
* `clientVersion` - _optional_ - The client version making the call.
Schema: `domain/type/version` (e.g., `google.com/intellij/v1`).
* `debuggeeId` - _required_ - ID of the debuggee whose breakpoint to get.
* `callback` - _optional_ - JSONP
* `fields` - _optional_ - Selector specifying which fields to include in a partial response.
* `key` - _optional_ - API key. Your API key identifies your project and provides you with API access, quota, and reports. Required unless you provide an OAuth 2.0 token.
* `oauth_token` - _optional_ - OAuth 2.0 token for the current user.
* `prettyPrint` - _optional_ - Returns response with indentations and line breaks.
* `quotaUser` - _optional_ - Available to use for quota purposes for server-side applications. Can be any arbitrary string assigned to a user, but should not exceed 40 characters.
* `uploadType` - _optional_ - Legacy upload protocol for media (e.g. "media", "multipart").
* `upload_protocol` - _optional_ - Upload protocol for media (e.g. "raw", "multipart").

## License

**flow**ground :- Telekom iPaaS / googleapis-com-clouddebugger-connector<br/>
Copyright © 2019, [Deutsche Telekom AG](https://www.telekom.de)<br/>
contact: flowground@telekom.de

All files of this connector are licensed under the Apache 2.0 License. For details
see the file LICENSE on the toplevel directory.
