# Import & Export

To explain the imports and exports rules, we use the following folder structure as example:

```
src/
    groups/
        builders.ts
        index.ts
        interfaces.ts
        models.ts
        utils.ts
    permissions/
        builders.ts
        index.ts
        interfaces.ts
        models.ts
    users/
        builders.ts
        index.ts
        interfaces.ts
        models.ts
```

Keep in mind that the `src` folder has an import alias (`@/`) and the project has external dependencies like `@fake/common` and `fake-utils`.

## Imports

### Path

When a folder is considered a [module](/naming-conventions#modules), every import inside it must be referred to the file directly. Imports from others modules have to use an import alias, if available, or import from the module folder anyway.

```typescript
// src/groups/models.ts
import { IUser } from "@/users";

import { IGroup } from "./interfaces";
```

### Order

Imports must be ordered alphabetically based on the _from_ property and separated with an empty line by level: external dependecies, aliases and different modules, current folder or module. Entities between brackets must be ordered alphabetically too.

```typescript
// src/groups/models.ts
import { Alt, Ctrl, Del } from "@fake/common";
import { firstOrDefault, mabBy } from "fake-utils";

import { IPermission } from "@/permission";
import { IUser, UserFactory } from "@/users";

import { IGroup } from "./interfaces";
import { addPermission, removePermission } from "./utils";
```

## Exports

See the [module](/naming-conventions#modules) section to know what to export from a folder and how to use from the outside.

### Inline

Exports must be defined inline, avoid to group them at the end of the file.

```typescript
const DelegateDefault: Delegate = () => Promise.resolve();

export function getDelegateOrDefault(handler: Handler): Delegate {
  return handler.delegate || DelegateDefault;
}

type Delegate = () => Promise<void>;
type Handler = { id: string; delegate?: Delegate };
```

### Order

Exports must be ordered alphabetically based on the _from_ property without any separation. Entities between brackets must be ordered alphabetically too.

```typescript
// src/groups/index.ts
export * from "./builders";
export { IGroup, IGroupFactory } from "./interfaces";
```
