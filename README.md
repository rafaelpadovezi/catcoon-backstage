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