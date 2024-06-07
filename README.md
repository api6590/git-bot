# EIP-Bot

EIP-Bot is a tool designed to automate the process of linting Ethereum Improvement Proposals (EIPs), identifying common errors, and auto-merging pull requests (PRs) when all tests pass. This README provides a detailed guide on the recent changes made to the project, specifically the addition of the `generatePRTitle` function, the logic behind it, and the problem it solves.

## Problem Statement

When creating pull requests for EIPs, it is essential to have a consistent and informative PR title. The title should include the EIP number and a brief description of the change. Manually generating these titles can be error-prone and inconsistent. To address this, we have introduced a `generatePRTitle` function that automates the generation of PR titles, ensuring consistency and accuracy.

## Changes and Logic

### 1. Create the `generatePRTitle` Function

The `generatePRTitle` function is designed to generate a PR title based on the EIP number and a brief description of the change. The function is implemented in TypeScript and is located in the `src/utils` directory.

#### Implementation

```typescript
// src/utils/generatePRTitle.ts

/**
 * Generates a PR title based on the EIP number and description.
 * @param eipNumber - The EIP number.
 * @param description - A brief description of the change.
 * @returns The formatted PR title.
 */
export function generatePRTitle(eipNumber: number, description: string): string {
  return `Update EIP-${eipNumber}: ${description}`;
}
```

### 2. Write Test Cases for the Function

To ensure the `generatePRTitle` function works as expected, we have written test cases using Jest. The test cases are located in the `src/utils` directory.

#### Test Cases

```typescript
// src/utils/generatePRTitle.test.ts

import { generatePRTitle } from './generatePRTitle';

describe('generatePRTitle', () => {
  it('should generate a PR title with the correct format', () => {
    const eipNumber = 3540;
    const description = 'EVM Object Format (EOF)';
    const expectedTitle = 'Update EIP-3540: EVM Object Format (EOF)';
    expect(generatePRTitle(eipNumber, description)).toBe(expectedTitle);
  });

  // Add more test cases as needed
});
```

### 3. Integrate the Function into the Main Logic
The `generatePRTitle` function is integrated into the main logic of the EIP-Bot. Specifically, it is used in the main.ts file to generate PR titles when processing pull requests.

#### Integration
```typescript
import { generatePRTitle } from './utils/generatePRTitle';

// Example usage
const eipNumber = 3540;
const description = 'EVM Object Format (EOF)';
const prTitle = generatePRTitle(eipNumber, description);
console.log(prTitle); // Output: "Update EIP-3540: EVM Object Format (EOF)"
```

### 4. Update the package.json File
To ensure that the tests can be run, update the package.json file to include the necessary scripts and dependencies.

