# [Catcoon Backstage](https://backstage.io)

Proof of concept Backstage developer portal created to the ficticional organization `catcoon-inc`.

## Step by step:

```sh
npx @backstage/create-app
```

To start the app, run:

```sh
yarn install
yarn dev
```

### Configure postgres

```sh
yarn add --cwd packages/backend pg
```

Using `app-config.local` to store connection information as suggested [here](https://github.com/backstage/backstage/issues/2521#issuecomment-694934491).

After running the app again the following dbs were created:

```
 backstage_plugin_catalog
 backstage_plugin_scaffolder
 backstage_plugin_auth
 backstage_plugin_search
```

### Auth - using Github

#### Import Groups and Users from github organization: https://backstage.io/docs/integrations/github/org

Install Github Org Entity Provider and add the setup code to the `catalog.ts`.
```sh
yarn add --cwd packages/backend @backstage/plugin-catalog-backend-module-github
```

When using a PAT, requires the following permissions: 

- `read:org`
- `read:user`
- `user:email`

#### Login with Github

Three steps are required:
- Configure the OAuth App on [Github](https://github.com/settings/developers) and add the configuration to the config files
- Add sign-in option to the frontend.
- In the backend, use the `usernameMatchingUserEntityName` as an identity provider.

### Plugins

#### Azure Devops (Pipelines)

##### Backend

Following https://github.com/backstage/backstage/tree/master/plugins/azure-devops-backend

```sh
cd packages/backend
yarn add @backstage/plugin-azure-devops-backend
```

After all changes, check the health of the plugin: http://localhost:7007/api/azure-devops/health

##### Frontend

Following https://github.com/backstage/backstage/tree/master/plugins/azure-devops

```sh
# From Backstage root directory
yarn add --cwd packages/app @backstage/plugin-azure-devops
```

And update frontend files