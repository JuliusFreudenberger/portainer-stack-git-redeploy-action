# Portainer stack redeploy action

This action allows you to update the stack with pull new images if you can't use webhooks. For example, in Portainer Community Edition.
This is a fork of [wirgen/portainer-stack-redeploy-action](https://github.com/wirgen/portainer-stack-redeploy-action) which allows to update stack deployed with a git repository hosting the `docker-compose.yaml`.

## Inputs

### `portainerUrl`

**Required** URL to the application instance. For example, https://example.com:9443

### `accessToken`

**Required** Token for API requests, can be created on the page https://example.com:9443/#!/account/tokens/new

### `stackId`

**Required** ID of stack to be updated. Must be integer

### `endpointId`

ID of endpoint (environment). Required if your stack is not in local environment

### `repositoryAuthentication`

Use stored credentials to pull docker-compose.yaml from git repository. When credentials are stored, but this is not set to `true`, the action will fail

### `environment`

Environment variables to set on the stack. When omitted, all existing variables will be cleared from the stack. Must be input as a JSON String; one array of objects each with the keys `name` and `value`

## Example usage

```yaml
uses:  JuliusFreudenberger/portainer-stack-git-redeploy-action@v1.0
with:
  portainerUrl: 'https://example.com:9443'
  accessToken: 'ptr_XXXyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyy'
  stackId: 8
  endpointId: 3
  environment: '[{"name":"image_version","value":"xxx"}]'
```
