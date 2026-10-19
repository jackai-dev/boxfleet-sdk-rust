# BoxFleet Rust API

<!-- omniwrap-api-reference eyJjb250cmFjdF9maW5nZXJwcmludCI6IjczZGVjMDgzOTQyOGYzOTg1NzhkZmM5ODZmNDc3ODZmNTMwYzZkMWE1Y2VlNjM2MGJmY2UxZDAwN2ViNjY1MzYiLCJvcGVyYXRpb25fY291bnQiOjI1LCJyZW5kZXJlciI6InJ1c3QiLCJ2ZXJzaW9uIjoiMS40LjAifQ -->

This generated index is tied to Semantic IR `1.14.0` and contract fingerprint `73dec0839428f398578dfc986f47786f530c6d1a5cee6360bfce1d007eb66536`. Every operation below is rendered from the same semantic contract and artifact-attested public member allocation as the SDK.

SDK maturity: **experimental**  
Artifact evidence: [`omniwrap-artifact.json`](omniwrap-artifact.json) binds this file by SHA-256 and is revalidated by the package gate.

## Client hooks and tracing

`ClientBuilder::hooks(RequestHooks::new()...)` registers four callbacks. Every attempt starts with `before_request` and ends with exactly one of `on_retry` (another attempt follows), `after_response` (the success the call returns) or `on_error` (the failure the call reports). Each receives the operation id, the HTTP method, the URL, the request headers, the attempt number (from 1), the time elapsed since the call started and, once the server answered, the HTTP status. No context carries a credential: `Authorization`, `Proxy-Authorization`, `Cookie`, every API-key header and API-key query parameter, and any configured credential value read `[redacted]`. Every hook borrows an immutable `HookContext`: no hook can change the request.

`ClientBuilder::tracer(...)` opens one span per call through the tracer interface this SDK defines, named after the operation id, with `http.request.method`, `http.response.status_code` and `http.request.resend_count`. It needs no tracing library; README.md maps it onto the OpenTelemetry API.

## Shared types

- `CapabilitiesResponse`
- `CloudBox`
- `CloudBoxActionRequest`
- `CloudBoxActionResponse`
- `CloudBoxEnvelope`
- `CloudBoxListResponse`
- `CreateCloudBoxRequest`
- `FleetPolicyUpdateRequest`
- `HealthResponse`
- `InspectProjectRequest`
- `JobExecutionResponse`
- `JobListResponse`
- `JobLogsResponse`
- `JobSummary`
- `ModsCatalogResponse`
- `OrganizationFleetResponse`
- `OrganizationMember`
- `OrganizationMembersResponse`
- `ProjectInspectionPlan`
- `ProvidersResponse`
- `SaasPlansResponse`
- `StartAgentJobRequest`
- `StartGithubJobRequest`
- `StartProjectJobRequest`
- `SyncCloudBoxVaultRequest`
- `SyncCloudBoxVaultResponse`
- `UpsertOrganizationMemberRequest`
- `WaitlistListResponse`
- `WaitlistRegisterRequest`
- `WaitlistRegisterResponse`
- `WhiteLabelCloudCatalog`

## Resource `cloud`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJjcmVhdGVfY2xvdWRfYm94IiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImNyZWF0ZUNsb3VkQm94IiwicGF0aCI6Ii92MS9jbG91ZC9ib3hlcyIsInJlc291cmNlIjoiY2xvdWQiLCJzZWN0aW9uX3NoYTI1NiI6ImE0MjU3MjA0M2RkZTQ0MWY1OTg3Y2U1NmI4ZDQ1M2YwMTBkZTRlNDcxMTQ2OWU3OTk5M2E4NWNmMmI4NzQ1ZDgiLCJzaWduYXR1cmVfc2hhMjU2IjoiYTRlNGNmMmU0NmQ3NWFmYzJiZGZmY2U3MzAyZjljZDMwYmQ4ZGY5YWJiMDBkMmUyNzI5OTgxOTVhMzA5Mjk0YyJ9 -->
### `client.create_cloud_box`

Operation ID: `createCloudBox`  
Route: `POST` `/v1/cloud/boxes`  

#### Signature

```rust
pub async fn create_cloud_box(&self, body: CreateCloudBoxRequest, request_options: Option<RequestOptions>) -> Result<CloudBoxEnvelope, ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `CreateCloudBoxRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `201` | Provisioned white-label box | application/json (CloudBoxEnvelope) |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjcmVhdGVDbG91ZEJveCJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJnZXRfd2hpdGVfbGFiZWxfY2xvdWRfY2F0YWxvZyIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6ImdldFdoaXRlTGFiZWxDbG91ZENhdGFsb2ciLCJwYXRoIjoiL3YxL2Nsb3VkL2NhdGFsb2ciLCJyZXNvdXJjZSI6ImNsb3VkIiwic2VjdGlvbl9zaGEyNTYiOiIwOTJhMTUxOTBlYzc5MWUyY2U1YjA5OWMwYmFkNzA4ZWRlNjJlZjljYjNjMTQ5MmVlNTU4ODM5MTliNjAwMmQ2Iiwic2lnbmF0dXJlX3NoYTI1NiI6IjhhN2JhODIyOTQ2ZmRkODJhODYwYjk5Njg3YmYyNTA2OGRhYjAzYTg2ODczMGFmZTIzMDMzMjE1YTg4MTM5MDMifQ -->
### `client.get_white_label_cloud_catalog`

Operation ID: `getWhiteLabelCloudCatalog`  
Route: `GET` `/v1/cloud/catalog`  

#### Signature

```rust
pub async fn get_white_label_cloud_catalog(&self, request_options: Option<RequestOptions>) -> Result<WhiteLabelCloudCatalog, ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | White-Label Cloud catalog | application/json (WhiteLabelCloudCatalog) |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRXaGl0ZUxhYmVsQ2xvdWRDYXRhbG9nIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJsaXN0X2Nsb3VkX2JveGVzIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoibGlzdENsb3VkQm94ZXMiLCJwYXRoIjoiL3YxL2Nsb3VkL2JveGVzIiwicmVzb3VyY2UiOiJjbG91ZCIsInNlY3Rpb25fc2hhMjU2IjoiODYxMzE1MmE0YzczNmFjMWQ4NWRjZTQ2NjJhYjk2MDRjNWZkNzVjZGIwOWExYWFkMWEzMTRlNjFkMDNiNzZlMiIsInNpZ25hdHVyZV9zaGEyNTYiOiJhMTZjYWY5NTYzYjVlNjI5YjkzZDYxNTg1MjQxODk0NWFmMjllMTQ0MDUzOTczNTI3YTZjZWMxNGVkNTU5OGM0In0 -->
### `client.list_cloud_boxes`

Operation ID: `listCloudBoxes`  
Route: `GET` `/v1/cloud/boxes`  

#### Signature

```rust
pub async fn list_cloud_boxes(&self, request_options: Option<RequestOptions>) -> Result<CloudBoxListResponse, ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | White-label cloud boxes | application/json (CloudBoxListResponse) |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0Q2xvdWRCb3hlcyJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJwZXJmb3JtX2Nsb3VkX2JveF9hY3Rpb24iLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoicGVyZm9ybUNsb3VkQm94QWN0aW9uIiwicGF0aCI6Ii92MS9jbG91ZC9ib3hlcy97Ym94SWR9L2FjdGlvbiIsInJlc291cmNlIjoiY2xvdWQiLCJzZWN0aW9uX3NoYTI1NiI6ImE3YmYzOTU0Y2Q0MmJkN2VjZmYwODFkOTFhZjEwN2E0ZTJjMTEwM2E2MzIwOGViYzNiNjFmOTgwNmIzNTIzZmQiLCJzaWduYXR1cmVfc2hhMjU2IjoiYmI2ODNkZWQ2Y2Y5NTU4MjcyMmJmYmE5YWYwODViZGU3Y2M2MjVlMzFkODhlNzQ4MGU5OWFiNzQzOTBhYjYzYSJ9 -->
### `client.perform_cloud_box_action`

Operation ID: `performCloudBoxAction`  
Route: `POST` `/v1/cloud/boxes/{boxId}/action`  

#### Signature

```rust
pub async fn perform_cloud_box_action(&self, box_id: String, body: CloudBoxActionRequest, request_options: Option<RequestOptions>) -> Result<CloudBoxActionResponse, ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `boxId` | `path` | yes | `string` |  |
| `body` | body | yes | `CloudBoxActionRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Cloud box action result | application/json (CloudBoxActionResponse) |

#### Canonical required-input example

```json
{
  "body": {
    "action": "suspend"
  },
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "boxId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJwZXJmb3JtQ2xvdWRCb3hBY3Rpb24ifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJzeW5jX2Nsb3VkX2JveF92YXVsdCIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJzeW5jQ2xvdWRCb3hWYXVsdCIsInBhdGgiOiIvdjEvY2xvdWQvYm94ZXMve2JveElkfS92YXVsdCIsInJlc291cmNlIjoiY2xvdWQiLCJzZWN0aW9uX3NoYTI1NiI6Ijk2Y2Q4YTU1MjUwYTQzZWU1YzE5NGRhMWMyNjE0ZGNkOWIzNDJmYWY1NzllMTI1YTgwMzczNGM2OTA4ODFiMzEiLCJzaWduYXR1cmVfc2hhMjU2IjoiNjgzOGZhZDRhZTBhMzkyYjM2MmQ2MzE1NmQ4NmYxOTZkMzljZDEyZjdlNjIzODI2Njg1YjUzOTY0NzY5OWYwMCJ9 -->
### `client.sync_cloud_box_vault`

Operation ID: `syncCloudBoxVault`  
Route: `POST` `/v1/cloud/boxes/{boxId}/vault`  

#### Signature

```rust
pub async fn sync_cloud_box_vault(&self, box_id: String, body: SyncCloudBoxVaultRequest, request_options: Option<RequestOptions>) -> Result<SyncCloudBoxVaultResponse, ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `boxId` | `path` | yes | `string` |  |
| `body` | body | yes | `SyncCloudBoxVaultRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Vault sync receipt (key names only, zero secret values echoed) | application/json (SyncCloudBoxVaultResponse) |

#### Canonical required-input example

```json
{
  "body": {
    "keys": [
      "example"
    ]
  },
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "boxId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJzeW5jQ2xvdWRCb3hWYXVsdCJ9 -->

## Resource `fleet`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJnZXRfb3JnYW5pemF0aW9uX2ZsZWV0IiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0T3JnYW5pemF0aW9uRmxlZXQiLCJwYXRoIjoiL3YxL29yZ2FuaXphdGlvbnMve29yZ0lkfS9mbGVldCIsInJlc291cmNlIjoiZmxlZXQiLCJzZWN0aW9uX3NoYTI1NiI6IjBlNDg1M2YyMTE1YTgzMzNhNzIzN2JlNTJkNzFjOTBlN2JmYWI2MzQwODRiNjBmYzE2NzFlMzU5MjkzM2RjMzgiLCJzaWduYXR1cmVfc2hhMjU2IjoiYmIyYjEzMzRmYzY1MGZjMmI3ZDU5MWY3Y2RkMzhlNzgyNjczNGY0NDQxODQyYWVmYTBmMjA0ZjM2YWYxOTI4YSJ9 -->
### `client.get_organization_fleet`

Operation ID: `getOrganizationFleet`  
Route: `GET` `/v1/organizations/{orgId}/fleet`  

#### Signature

```rust
pub async fn get_organization_fleet(&self, org_id: String, request_options: Option<RequestOptions>) -> Result<OrganizationFleetResponse, ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `orgId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Organization fleet park overview | application/json (OrganizationFleetResponse) |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "orgId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRPcmdhbml6YXRpb25GbGVldCJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJsaXN0X29yZ2FuaXphdGlvbl9tZW1iZXJzIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoibGlzdE9yZ2FuaXphdGlvbk1lbWJlcnMiLCJwYXRoIjoiL3YxL29yZ2FuaXphdGlvbnMve29yZ0lkfS9tZW1iZXJzIiwicmVzb3VyY2UiOiJmbGVldCIsInNlY3Rpb25fc2hhMjU2IjoiMWE1NDQ4ZGEwYzBkNGQwMTg4MDJkZGE2Y2ViNTM0ZjhiMjFkODI1Y2E0NjcwOTkwZGFhMGFmODg0Mzc5YTUzMCIsInNpZ25hdHVyZV9zaGEyNTYiOiI5ZWJiYTQwY2QwNzM1MjE5MjY3OWFjNTU4YzFkMWQxNWZmZjE4MTk2ZjU1OTJmZTVmMmQ3ZDZiOWU1MDJmYTczIn0 -->
### `client.list_organization_members`

Operation ID: `listOrganizationMembers`  
Route: `GET` `/v1/organizations/{orgId}/members`  

#### Signature

```rust
pub async fn list_organization_members(&self, org_id: String, request_options: Option<RequestOptions>) -> Result<OrganizationMembersResponse, ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `orgId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Organization members list | application/json (OrganizationMembersResponse) |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "orgId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0T3JnYW5pemF0aW9uTWVtYmVycyJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJsaXN0X3NhYXNfcGxhbnMiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJsaXN0U2Fhc1BsYW5zIiwicGF0aCI6Ii92MS9zYWFzL3BsYW5zIiwicmVzb3VyY2UiOiJmbGVldCIsInNlY3Rpb25fc2hhMjU2IjoiNmJjNDAxMTlkNDM3ZGM3MGIyMDFhMzE0YjQ1Mzg1MTFhNTZkOTlkNGNmMjBkNjgzMmIyNDg4ZDFmOWJhZmQzZCIsInNpZ25hdHVyZV9zaGEyNTYiOiIzODAxZjdmMTA4MWFmNTU4NTExOThmZGYzZGYzZDU2MWI0ZjY2ZTc3NTMxMTRhNDA0ZjQwMTllYmExYmI3MGJmIn0 -->
### `client.list_saas_plans`

Operation ID: `listSaasPlans`  
Route: `GET` `/v1/saas/plans`  

#### Signature

```rust
pub async fn list_saas_plans(&self, request_options: Option<RequestOptions>) -> Result<SaasPlansResponse, ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | SaaS plan catalog | application/json (SaasPlansResponse) |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0U2Fhc1BsYW5zIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJsaXN0X3dhaXRsaXN0X2ludml0ZXMiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJsaXN0V2FpdGxpc3RJbnZpdGVzIiwicGF0aCI6Ii92MS93YWl0bGlzdCIsInJlc291cmNlIjoiZmxlZXQiLCJzZWN0aW9uX3NoYTI1NiI6IjQzYjU1Yjg2NjE2OTAxMThjZjQ4YThmOTJjODZhNWUzMTNiYTYwNmI1YTY0ZDJjYjBmYTAxYWU4MTQzZGUxNTUiLCJzaWduYXR1cmVfc2hhMjU2IjoiZGNkNTk5MjRmNTEwNzFiZGRiNzgzNTBkYjM3YWY5YzRlZTA0OTViYmZhYjA1ZDZlZTk5NzM3ODJmNWFiZDYzYSJ9 -->
### `client.list_waitlist_invites`

Operation ID: `listWaitlistInvites`  
Route: `GET` `/v1/waitlist`  

#### Signature

```rust
pub async fn list_waitlist_invites(&self, limit: Option<i64>, format: Option<ListWaitlistInvitesFormat>, request_options: Option<RequestOptions>) -> Result<WaitlistListResponse, ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `limit` | `query` | no | `integer` |  |
| `format` | `query` | no | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Waitlist invitations list | application/json (WaitlistListResponse) |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0V2FpdGxpc3RJbnZpdGVzIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJyZWdpc3Rlcl93YWl0bGlzdF9pbnZpdGUiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoicmVnaXN0ZXJXYWl0bGlzdEludml0ZSIsInBhdGgiOiIvdjEvd2FpdGxpc3QiLCJyZXNvdXJjZSI6ImZsZWV0Iiwic2VjdGlvbl9zaGEyNTYiOiI2NmYxYWJiMGVjZTkzMDkyMTAwY2I5NTA1OWU3MWViYjAyMTk2MmM0NjE1YTA4YWE0Zjg2NjIzYTZkNGEyOGI4Iiwic2lnbmF0dXJlX3NoYTI1NiI6IjVjNzE2ZmZkMDE1MzE3NDlkNWJiOTEyMDQ2YWI5OWI1MGYyZmVhNGMyMjE0ZTJiMGQ3ODJkNDhiYWI2Mjg1NGMifQ -->
### `client.register_waitlist_invite`

Operation ID: `registerWaitlistInvite`  
Route: `POST` `/v1/waitlist`  

#### Signature

```rust
pub async fn register_waitlist_invite(&self, body: WaitlistRegisterRequest, request_options: Option<RequestOptions>) -> Result<WaitlistRegisterResponse, ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `WaitlistRegisterRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `201` | Waitlist registration recorded in boxfleet.waitlist_invites | application/json (WaitlistRegisterResponse) |

#### Canonical required-input example

```json
{
  "body": {
    "email": "example-9266@example.test"
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJyZWdpc3RlcldhaXRsaXN0SW52aXRlIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJ1cGRhdGVfb3JnYW5pemF0aW9uX2ZsZWV0X3BvbGljeSIsIm1ldGhvZCI6IlBVVCIsIm9wZXJhdGlvbl9pZCI6InVwZGF0ZU9yZ2FuaXphdGlvbkZsZWV0UG9saWN5IiwicGF0aCI6Ii92MS9vcmdhbml6YXRpb25zL3tvcmdJZH0vZmxlZXQvcG9saWN5IiwicmVzb3VyY2UiOiJmbGVldCIsInNlY3Rpb25fc2hhMjU2IjoiMjY5NjQxZGFkNTM4MWU1NDIzNWQ3YjA1YTI0NDVhYzE5YWExNjNhNDE1YjNmOTdlM2YzOGY1ZmMzMTRhMTdkYiIsInNpZ25hdHVyZV9zaGEyNTYiOiIxZDVlN2NmYTkzYjU3ZWUyOWQzMDFkZjQ0MjkzMDc0Y2E0ZGM1YjE3NjVlZTg3MzI5NDdhNDg0ZmNmNTE5MjNmIn0 -->
### `client.update_organization_fleet_policy`

Operation ID: `updateOrganizationFleetPolicy`  
Route: `PUT` `/v1/organizations/{orgId}/fleet/policy`  

#### Signature

```rust
pub async fn update_organization_fleet_policy(&self, org_id: String, body: FleetPolicyUpdateRequest, request_options: Option<RequestOptions>) -> Result<OrganizationFleetResponse, ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `orgId` | `path` | yes | `string` |  |
| `body` | body | yes | `FleetPolicyUpdateRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Updated fleet policy | application/json (OrganizationFleetResponse) |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "orgId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJ1cGRhdGVPcmdhbml6YXRpb25GbGVldFBvbGljeSJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJ1cHNlcnRfb3JnYW5pemF0aW9uX21lbWJlciIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJ1cHNlcnRPcmdhbml6YXRpb25NZW1iZXIiLCJwYXRoIjoiL3YxL29yZ2FuaXphdGlvbnMve29yZ0lkfS9tZW1iZXJzIiwicmVzb3VyY2UiOiJmbGVldCIsInNlY3Rpb25fc2hhMjU2IjoiMWMyYzQ3Y2RhYmFiNjJkMjdiYzcwM2I0MjRiZjA3ZjAxZDkyZGNiNTM0NDg0NTM0NDcyZGNkNTk4MzQ3NmFiMSIsInNpZ25hdHVyZV9zaGEyNTYiOiJmMzQ4MmZhZWQ0NzNkNjdiZTMwMjUzMmRjNWE4ZjdjZDJiODc3NDg3ODI5NTZiMDQ3MGY2YzkyNWY4M2Y3NjM4In0 -->
### `client.upsert_organization_member`

Operation ID: `upsertOrganizationMember`  
Route: `POST` `/v1/organizations/{orgId}/members`  

#### Signature

```rust
pub async fn upsert_organization_member(&self, org_id: String, body: UpsertOrganizationMemberRequest, request_options: Option<RequestOptions>) -> Result<OrganizationMember, ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `orgId` | `path` | yes | `string` |  |
| `body` | body | yes | `UpsertOrganizationMemberRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Upserted organization member | application/json (OrganizationMember) |

#### Canonical required-input example

```json
{
  "body": {
    "email": "example",
    "role": "owner",
    "userId": "example"
  },
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "orgId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJ1cHNlcnRPcmdhbml6YXRpb25NZW1iZXIifQ -->

## Resource `jobs`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJjYW5jZWxfam9iIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImNhbmNlbEpvYiIsInBhdGgiOiIvdjEvam9icy97am9iSWR9L2NhbmNlbCIsInJlc291cmNlIjoiam9icyIsInNlY3Rpb25fc2hhMjU2IjoiYTE4NjViMTlmODQ1OGJiNjk0NzU5NjA3MTAxOTM0NGIxYTI2NjE1ZTFlNzZjMmRlM2M1ODcxZjE2NDhlODQzNSIsInNpZ25hdHVyZV9zaGEyNTYiOiI4MWUxODhhZjBiYzE5ZmRlOGRjNDY2ZGZmYzcyZjdmYTYxMzM1MjEwNjRkZmQyNzU2YzQ5ZmE3ZDU1NTBlOTAzIn0 -->
### `client.cancel_job`

Operation ID: `cancelJob`  
Route: `POST` `/v1/jobs/{jobId}/cancel`  

#### Signature

```rust
pub async fn cancel_job(&self, job_id: String, request_options: Option<RequestOptions>) -> Result<JobSummary, ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `jobId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Cancellation result | application/json (JobSummary) |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "jobId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjYW5jZWxKb2IifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJnZXRfam9iX2V4ZWN1dGlvbiIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6ImdldEpvYkV4ZWN1dGlvbiIsInBhdGgiOiIvdjEvam9icy97am9iSWR9L2V4ZWN1dGlvbiIsInJlc291cmNlIjoiam9icyIsInNlY3Rpb25fc2hhMjU2IjoiNTQxYTQ2OGM1ZDQ4ZDFiY2FlNzk5MDU3YWFiYmM0ODI0ZWM3NmQyMDMzNTBlNjgzNGE1ZDg4MmQ1MmRjNzZkNyIsInNpZ25hdHVyZV9zaGEyNTYiOiIzOTliZDIxMTU3NWQxZmQ2YWNlZmQ1ZTdjZWViMzJmNjUwYzJiYzM0MWIyMDU1YTQ2ZjMwNGMwODU1YWE0MzUyIn0 -->
### `client.get_job_execution`

Operation ID: `getJobExecution`  
Route: `GET` `/v1/jobs/{jobId}/execution`  

#### Signature

```rust
pub async fn get_job_execution(&self, job_id: String, request_options: Option<RequestOptions>) -> Result<JobExecutionResponse, ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `jobId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Job execution evidence | application/json (JobExecutionResponse) |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "jobId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRKb2JFeGVjdXRpb24ifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJnZXRfam9iX2xvZ3MiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJnZXRKb2JMb2dzIiwicGF0aCI6Ii92MS9qb2JzL3tqb2JJZH0vbG9ncyIsInJlc291cmNlIjoiam9icyIsInNlY3Rpb25fc2hhMjU2IjoiYmRhNTU2ZTI3ZjNlODU5MTNhZDdkYTExZGU1MWMwNWIxNGYxNmQ1ZmJkYWRkYTZlNDM2NGQ1YzE5YTU4MWU0NSIsInNpZ25hdHVyZV9zaGEyNTYiOiJhYjkzNTk1YTI0M2QyZWQ1ZmM1OTliYjkxY2VjNWY2Zjk3MGM2YzNhNzEyYThhYjdlZjJjZGJhMDBlMDNhNGU1In0 -->
### `client.get_job_logs`

Operation ID: `getJobLogs`  
Route: `GET` `/v1/jobs/{jobId}/logs`  

#### Signature

```rust
pub async fn get_job_logs(&self, job_id: String, request_options: Option<RequestOptions>) -> Result<JobLogsResponse, ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `jobId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Redacted job logs | application/json (JobLogsResponse) |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "jobId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRKb2JMb2dzIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJnZXRfam9iX3N0YXR1cyIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6ImdldEpvYlN0YXR1cyIsInBhdGgiOiIvdjEvam9icy97am9iSWR9IiwicmVzb3VyY2UiOiJqb2JzIiwic2VjdGlvbl9zaGEyNTYiOiI5NzhjMzhjNGQxZTIzYTA4MWUwNTNmNjMwMTYxMGFmZjYxOTMxMWY4YTIyZGY5NTdjYTEwMjU3MTZiM2U5M2Q4Iiwic2lnbmF0dXJlX3NoYTI1NiI6IjczOTc0M2MyYTViNGU0YjQwZmFkYWIzNTlhZmIxNjI2NDczNjdkZjIzNTE5OGI2MGI3OTU3NGU0OGUyOTBkNWIifQ -->
### `client.get_job_status`

Operation ID: `getJobStatus`  
Route: `GET` `/v1/jobs/{jobId}`  

#### Signature

```rust
pub async fn get_job_status(&self, job_id: String, request_options: Option<RequestOptions>) -> Result<JobSummary, ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `jobId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Job status snapshot | application/json (JobSummary) |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "jobId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRKb2JTdGF0dXMifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJpbnNwZWN0X3Byb2plY3QiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoiaW5zcGVjdFByb2plY3QiLCJwYXRoIjoiL3YxL2luc3BlY3QiLCJyZXNvdXJjZSI6ImpvYnMiLCJzZWN0aW9uX3NoYTI1NiI6ImEyYzRjMjViN2U0OGU0YjdlZjMzM2YyNmE2MDk4NzgyNzk2NGNlNTZhMWQxOTFlN2Y1ZmZkOTIxZDYwMDU2MWMiLCJzaWduYXR1cmVfc2hhMjU2IjoiNzIzYTViMDI1OTdjZTJkMjlkY2U3OWE0M2UyY2FhY2MwNDY4YmE5NzUwNGU4MDEyM2YzNjg3ZTFlMzIyYjY0MiJ9 -->
### `client.inspect_project`

Operation ID: `inspectProject`  
Route: `POST` `/v1/inspect`  

#### Signature

```rust
pub async fn inspect_project(&self, body: InspectProjectRequest, request_options: Option<RequestOptions>) -> Result<ProjectInspectionPlan, ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `InspectProjectRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Project inspection plan | application/json (ProjectInspectionPlan) |

#### Canonical required-input example

```json
{
  "body": {
    "projectRoot": "example"
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJpbnNwZWN0UHJvamVjdCJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJsaXN0X2pvYnMiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJsaXN0Sm9icyIsInBhdGgiOiIvdjEvam9icyIsInJlc291cmNlIjoiam9icyIsInNlY3Rpb25fc2hhMjU2IjoiNmJmNDY5OTEwMzE1Nzk2YWFlMzAzZTM1YjQ5NjBlZmMwZDA2ZjYyZmVhMGJhZmRmOTQ5YmMzN2ExY2MwMjRmNiIsInNpZ25hdHVyZV9zaGEyNTYiOiI1MGNiOTg0Mjg0MjMyZWExMDhmMGUwYjNlMzBiNzkzYjFiNTgwYzcxNWY5NWUwYTQ5YjBiYjM5MzM5NTc0NDc0In0 -->
### `client.list_jobs`

Operation ID: `listJobs`  
Route: `GET` `/v1/jobs`  

#### Signature

```rust
pub async fn list_jobs(&self, status_value: Option<ListJobsStatus>, box_id: Option<String>, limit: Option<i64>, request_options: Option<RequestOptions>) -> Result<JobListResponse, ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `status` | `query` | no | `string` |  |
| `boxId` | `query` | no | `string` |  |
| `limit` | `query` | no | `integer` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Paginated job list | application/json (JobListResponse) |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0Sm9icyJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJzdGFydF9hZ2VudF9qb2IiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoic3RhcnRBZ2VudEpvYiIsInBhdGgiOiIvdjEvYWdlbnQtam9icyIsInJlc291cmNlIjoiam9icyIsInNlY3Rpb25fc2hhMjU2IjoiOGZiYzNlZmM5YTI5NTZmMjg0M2U0ZDRjMjI1ZmVhM2VhNmY4NTAyN2UwNTBiYWJjNTBlYzY2YWM4YzYzZTNlZSIsInNpZ25hdHVyZV9zaGEyNTYiOiI4OTNhOGQzNGYyZDBiYzU4OWJlNWY1MmRiMWRmYWZhMTk4ZDUwOTk5NmQ3ZTM3NTBiZGRjMmFiNzdlYTVjZTgwIn0 -->
### `client.start_agent_job`

Operation ID: `startAgentJob`  
Route: `POST` `/v1/agent-jobs`  

#### Signature

```rust
pub async fn start_agent_job(&self, body: StartAgentJobRequest, request_options: Option<RequestOptions>) -> Result<JobSummary, ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `StartAgentJobRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `201` | Autonomous coding job started | application/json (JobSummary) |

#### Canonical required-input example

```json
{
  "body": {
    "projectRoot": "example",
    "task": "example"
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJzdGFydEFnZW50Sm9iIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJzdGFydF9naXRodWJfam9iIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6InN0YXJ0R2l0aHViSm9iIiwicGF0aCI6Ii92MS9naXRodWItam9icyIsInJlc291cmNlIjoiam9icyIsInNlY3Rpb25fc2hhMjU2IjoiNGUyMTNkNjg3OGRmMzgzZWJmODI2NzA4Yjc0N2RlMGYxZWQ3ZjIxYjcxYWU0ZmVhMzQzM2YwNzU1MGMxMTIwNSIsInNpZ25hdHVyZV9zaGEyNTYiOiJkOTBiNWZhYjcyY2VlNGVmYTYxODBjM2U1NzYwNTAzNWFlMTA2MTBlNDA1N2ZjMTJmNGExMmI2OWU0YTc2MTA0In0 -->
### `client.start_github_job`

Operation ID: `startGithubJob`  
Route: `POST` `/v1/github-jobs`  

#### Signature

```rust
pub async fn start_github_job(&self, body: StartGithubJobRequest, request_options: Option<RequestOptions>) -> Result<JobSummary, ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `StartGithubJobRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `201` | GitHub sandbox job started | application/json (JobSummary) |

#### Canonical required-input example

```json
{
  "body": {
    "repository": "example"
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJzdGFydEdpdGh1YkpvYiJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJzdGFydF9wcm9qZWN0X2pvYiIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJzdGFydFByb2plY3RKb2IiLCJwYXRoIjoiL3YxL2pvYnMiLCJyZXNvdXJjZSI6ImpvYnMiLCJzZWN0aW9uX3NoYTI1NiI6IjMyMDY3MmRmNWI2MWEwN2ViYzdhYzA2NzRjODdhZjNkNDNmNzRjZTA1M2UzMmI5NmZjZWJhMjE1YzgxNTBkMjUiLCJzaWduYXR1cmVfc2hhMjU2IjoiMjg1YzVjYWQ2NGVhZDljMDA5NzIxZDVjZDk3NjVhMGNkMzMzMjYyMDUxOTNiMzQzYjdkZTMxNWMzNjYzYjQ3ZCJ9 -->
### `client.start_project_job`

Operation ID: `startProjectJob`  
Route: `POST` `/v1/jobs`  

#### Signature

```rust
pub async fn start_project_job(&self, body: StartProjectJobRequest, request_options: Option<RequestOptions>) -> Result<JobSummary, ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `StartProjectJobRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `201` | Job created and started | application/json (JobSummary) |

#### Canonical required-input example

```json
{
  "body": {
    "projectRoot": "example"
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJzdGFydFByb2plY3RKb2IifQ -->

## Resource `system`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJkZXNjcmliZV9hZ2VudF9tb2RzIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZGVzY3JpYmVBZ2VudE1vZHMiLCJwYXRoIjoiL3YxL21vZHMiLCJyZXNvdXJjZSI6InN5c3RlbSIsInNlY3Rpb25fc2hhMjU2IjoiM2U1ZTVlZjg2NTRmMjUxMzAyOWI0ZWRkZDUwYTBkNjlhMDZiNDVhOTg3NTdlNGM2MDQzMzI5MGFhMGQwYTk0MCIsInNpZ25hdHVyZV9zaGEyNTYiOiJmODg5YTUzYTY5MDQzZDVhMTkwYTM5OGZlZmNkZDhkZjA1ODA5MDhmZjZiMDNmNTQyYjNmMjk4NmI4ZDU2YWUyIn0 -->
### `client.describe_agent_mods`

Operation ID: `describeAgentMods`  
Route: `GET` `/v1/mods`  

#### Signature

```rust
pub async fn describe_agent_mods(&self, target: Option<DescribeAgentModsTarget>, request_options: Option<RequestOptions>) -> Result<ModsCatalogResponse, ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `target` | `query` | no | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Agent mods catalog | application/json (ModsCatalogResponse) |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJkZXNjcmliZUFnZW50TW9kcyJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJnZXRfaGVhbHRoIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0SGVhbHRoIiwicGF0aCI6Ii9oZWFsdGgiLCJyZXNvdXJjZSI6InN5c3RlbSIsInNlY3Rpb25fc2hhMjU2IjoiMTlmN2M2MTU1YTEzN2QxMGEzOWUyYzhhZWZkZDQ3YTMxZjUzYWFiNDAxZjViNTc2MjY4YWIwY2JkMzRjNTQwZiIsInNpZ25hdHVyZV9zaGEyNTYiOiI5N2VmYjE4MWYyZWQ3Mjc3ZDdmZDUyMzk0ODc3MDM0MjhhMjA1MjljNDhlNDY3ZmM2NTQzM2M3NDQxNjhhNmZjIn0 -->
### `client.get_health`

Operation ID: `getHealth`  
Route: `GET` `/health`  

#### Signature

```rust
pub async fn get_health(&self, request_options: Option<RequestOptions>) -> Result<HealthResponse, ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Service health status | application/json (HealthResponse) |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRIZWFsdGgifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJsaXN0X2NhcGFiaWxpdGllcyIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6Imxpc3RDYXBhYmlsaXRpZXMiLCJwYXRoIjoiL3YxL2NhcGFiaWxpdGllcyIsInJlc291cmNlIjoic3lzdGVtIiwic2VjdGlvbl9zaGEyNTYiOiJlZWM5ZWUyMzAwZjQ4ZWFhNjc1ZTQ2MjgxYmFjZTRhNTEwM2U4ZjMxNmViZjg0NmVhYmYyMTJjZjhmZDg5ZTgyIiwic2lnbmF0dXJlX3NoYTI1NiI6ImFmNjUyZjBiNTNjMTJkMmMzNzFjNGFlYjE0M2E1MDQ5NDcwM2M2Njc4ZjA5MDRhOGFhYWEyMjdjZjk4NzQxMDYifQ -->
### `client.list_capabilities`

Operation ID: `listCapabilities`  
Route: `GET` `/v1/capabilities`  

#### Signature

```rust
pub async fn list_capabilities(&self, query_value: Option<String>, state: Option<ListCapabilitiesState>, request_options: Option<RequestOptions>) -> Result<CapabilitiesResponse, ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `query` | `query` | no | `string` |  |
| `state` | `query` | no | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Capability catalog and job limits | application/json (CapabilitiesResponse) |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0Q2FwYWJpbGl0aWVzIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6Imxhbmd1YWdlLWV4YW1wbGUtbm90LWdlbmVyYXRlZCIsImV4YW1wbGVfc3RhdHVzIjoidW5zdXBwb3J0ZWQiLCJtZW1iZXIiOiJsaXN0X3Byb3ZpZGVycyIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6Imxpc3RQcm92aWRlcnMiLCJwYXRoIjoiL3YxL3Byb3ZpZGVycyIsInJlc291cmNlIjoic3lzdGVtIiwic2VjdGlvbl9zaGEyNTYiOiIzZTc3ODFhZWVkMDRhNmU5ZTc5NzgwZWM5YTM4NDZjZDA2ODZjMGMyNTkzZjFiZGM3MTYzM2Q1MDIyNjgyMGE2Iiwic2lnbmF0dXJlX3NoYTI1NiI6ImVmY2E3ZjQwYmY4M2M4MDA4MmMyYzM5ZjMyMDIyMmNmMThmM2VmZTc0YjU3OGZhYWYzNjBmY2QyOTkwMTU0YTgifQ -->
### `client.list_providers`

Operation ID: `listProviders`  
Route: `GET` `/v1/providers`  

#### Signature

```rust
pub async fn list_providers(&self, request_options: Option<RequestOptions>) -> Result<ProvidersResponse, ApiError>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Provider list with runtime templates | application/json (ProvidersResponse) |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `unsupported`  
Unsupported reason: `language-example-not-generated`

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0UHJvdmlkZXJzIn0 -->

