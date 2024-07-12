# CloudFormation Helpers [![npm version](https://img.shields.io/npm/v/@nordicsemiconductor/cloudformation-helpers.svg)](https://www.npmjs.com/package/@nordicsemiconductor/cloudformation-helpers)

[![GitHub Actions](https://github.com/bifravst/cloudformation-helpers/workflows/Test%20and%20Release/badge.svg)](https://github.com/bifravst/cloudformation-helpers/actions)
[![semantic-release](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg)](https://github.com/semantic-release/semantic-release)
[![Renovate](https://img.shields.io/badge/renovate-enabled-brightgreen.svg)](https://renovatebot.com)
[![@commitlint/config-conventional](https://img.shields.io/badge/%40commitlint-config--conventional-brightgreen)](https://github.com/conventional-changelog/commitlint/tree/master/@commitlint/config-conventional)
[![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg)](https://github.com/prettier/prettier/)
[![ESLint: TypeScript](https://img.shields.io/badge/ESLint-TypeScript-blue.svg)](https://github.com/typescript-eslint/typescript-eslint)

Helper functions which simplify working with AWS CloudFormation stacks.

## Installation

    npm i --save-dev --save-exact @nordicsemiconductor/cloudformation-helpers

## Usage

### `cfnResponse`

`cfnResponse` implements sending custom resource responses.

```typescript
import {
  cfnResponse,
  ResponseStatus,
} from "@nordicsemiconductor/cloudformation-helpers";
import { CloudFormationCustomResourceEvent } from "aws-lambda";

/**
 * Lambda creating a custom resource
 */
export const handler = async (
  event: CloudFormationCustomResourceEvent,
): Promise<void> => {
  // Create custom resource ...

  await cfnResponse({
    Status: ResponseStatus.SUCCESS,
    event,
    PhysicalResourceId: "MyCustomResource",
  });
};
```
