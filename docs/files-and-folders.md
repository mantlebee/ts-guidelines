# Files and Folders

## Naming

Files and folders names must be [kebab-case](/naming-conventions#cases).

```
src/
    user-permissions/
        admin-permissions.ts
        base-permissions.ts
```

## Categorization

Inside a [module](/naming-conventions#modules), files could be scoped to a specific [entitiy](/naming-conventions#entities) or logic categorization, in this cases, categorizations are defined after a dot (`file-name.category.extension`).

#### Logic categorization

```
src/
    user-permissions/
        admin-permissions.debug.ts
        admin-permissions.release.ts
        base-permissions.debug.ts
        base-permissions.release.ts
```

#### Entities categorization

See the [File or Folder?](#file-or-folder) chapter for an improved example.

```
src/
    users/
        admin.interfaces.ts
        admin.models.ts
        base.interfaces.ts
        base.models.ts
```

#### Multiple categorizations

More categorizations can be concatenated.

```
src/
    users/
        admin.interfaces.private.ts
        admin.interfaces.public.ts
        admin.models.ts
        base.interfaces.private.ts
        base.interfaces.public.ts
        base.models.ts
```

## File or Folder?

When a logic needs to be separated into multiple files for a better maintenance, prefer always the use of a folder.
The following example improves the [Entities example](#entities-example) of the previous chapter. Categorizations could be used to separate entities available outside the module from the internal ones.

```
src/
    users/
        admin/
            index.ts
            interfaces.ts
            models.ts
        base/
            index.ts
            interfaces.ts
            models.ts
```

Categorization could be now used to separate entities available outside the module from the internal ones.

```
src/
    users/
        index.ts
        interfaces.private.ts
        interfaces.public.ts
        models.ts
```
