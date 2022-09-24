# ESLint issue sample

## How to reproduce the issue

- `npm i`
- `npm run lint`

No lint errors are displayed while I would expect to see something like:

- `5:1 error` @src/folderA/fileA1 `import should occur before import of` @src/folderB/fileB1 `import/order`

since I believe `fileA1` should be considered as `internal` and `fileB1` as parent.

### More scenarios

- No error (by `/* eslint-disable @dword-design/import-alias/prefer-alias */`)

```ts
import { z } from 'zod';
import { bar } from '@src/folderB/fileB1';
import { foo } from '../../folderA/fileA1';
```

- Error (by `/* eslint-disable @dword-design/import-alias/prefer-alias */`)

```ts
import { z } from 'zod';
import { foo } from '../../folderA/fileA1';
import { bar } from '@src/folderB/fileB1';
```

- No error (by `/* eslint-disable @dword-design/import-alias/prefer-alias */`)

```ts
import { z } from 'zod';
import { bar } from '../fileB1';
import { foo } from '../../folderA/fileA1';
```
