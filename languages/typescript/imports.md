# Imports

## Rules

1. Import statements **SHOULD** follow this order:
   1. Packages outside the workspace.
   2. Other packages in the same workspace.
   3. The same package.

## Applies to

TypeScript production code.

## Exceptions

None.

## Examples

### Good

```ts
import { useMemo } from "react";

import { HexColorUtils } from "@helpwave/hightide-design/utils";

import { useTheme } from "../theme/ThemeContext";
```

### Bad

```ts
import { useTheme } from "../theme/ThemeContext";

import { useMemo } from "react";
```
