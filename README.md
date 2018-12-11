# Helpers Addon for CMS

This addon combines a set of features that would improve the main functionality of the Cockpit CMS. The idea is to be including new helpers as they are required.

## Helpers

The current implementation provides:

- Password reset CLI command
- Singleton data export/import CLI command
- JSON Preview for collection entries
- Environment indicator
- Assets in modules menubar
- Quick actions

### Password reset

A CLI command that permits to reset the password of an user, e.g.:

```bash
./cp password --user "admin" --pass "admin"
```

### Singleton data export/import CLI command

A CLI command that permits to export and import singleton data, e.g.:

```bash
./cp export-singleton --name settings

Exporting data from singleton settings
Singleton settings exported to #storage:exports/singletons/settings.json - 4014 bytes written
```

To import just run the import-singleton command:

```bash
./cp import-singleton --name settings
Singleton settings data imported from #storage:exports/singletons/settings.json
```

**Notes:**
The #storage:exports/singletons folder is always used for exporting/importing.


### JSON preview of collection entries

A JSON Preview link on each colletion entry sidebar, so we can access the JSON that will be returned from the API directly from the form page, e.g.:

![JSON Preview](https://monosnap.com/image/AirWoZb65N22WNjPkiTyISr4JZxVLZ.png)

### Environment indicator

A simple mechanism to provide a visual feedback regarding the environment we are working, this can be useful to prevent doing changes on a live environment by mistake. To enable it just add to the `config.yaml`:

```yaml
helpers:
  environment: local
```

You can use local, dev, stg or prod and the you'll have an indicator in the cockpit site name and a border line in main header, e.g.:

**Local**

![Local Environment](https://monosnap.com/image/LBEIL3eeI6GaHlTnmkJAB047BDDlxA.png)

**Prod**

![Prod Environment](https://monosnap.com/image/hF6MDznnCQ1ahhAEhGdtsiLrW1dPtj.png)

### Assets in modules menu

The modules menu includes core Collections, Singletons and Forms, the Helpers addon makes a menu entry for Assets:

![Assets](https://monosnap.com/image/dq7InK3hqcckwcORLgUwl6Ulvyp6kc.png)

### Quick Actions

A simple UI element that is present in the modules navigation bar and can be configured (`config.yaml`) to display a list of quick actions. Actions can be aggregated in groups, and can be a link to whatever you need, for example:

```yaml
helpers:
  quickactions:
    - group: Create
      actions:
        - label: Post
          path: /collections/entry/post
        - label: Page
          path: /collections/entry/page
        - label: Categories
          path: /collections/entry/category
    - group: Accounts
      actions:
        - label: New
          path: /accounts/create
```

![Quick Action](https://monosnap.com/image/C50GMgiJ54dxNZKkoNfcu6Fma7YriC.png)

## Installation

1. Confirm that you have Cockpit CMS (Next branch) installed and working.
2. Download zip and extract to 'your-cockpit-docroot/addons' (e.g. cockpitcms/addons/Helpers)
   (Ensure that the addon folder is named Helpers)

## Copyright and license

Copyright 2018 pauloamgomes under the MIT license.
