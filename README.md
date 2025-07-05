# Algorand IDE Templates

This repository provides a collection of Algorand smart contract templates for various use cases, built with PyTeal/TealScript. These templates are designed to be easily integrated into an IDE environment, providing a quick starting point for developers.

## Contributing New Templates

We welcome contributions from the community! If you have a new Algorand smart contract template you'd like to share, please follow these guidelines:

### 1. Template Structure

Each template should reside in its own directory within the `playground/` folder. The directory name should be a "slug" (a URL-friendly, lowercase, hyphen-separated name) that uniquely identifies your template.

Inside your template's directory, you **must** create a `files.ts` file. This `files.ts` file will contain the file system tree for your template, as expected by `@webcontainer/api`.

**Example:**

If your template slug is `hello_world`, your directory structure should look like this:

```
playground/
└── hello_world/
    └── files.ts
```

The `files.ts` content should export a `tealScriptFiles` object, similar to the example provided in `GEMINI.md`:

```typescript
/** @satisfies {import('@webcontainer/api').FileSystemTree} */
export const tealScriptFiles = {
  src: {
    directory: {
      "main.algo.ts": {
        file: {
          contents: `// Your TealScript code here`
        }
      },
      // ... other files for your template
    }
  },
  // ... other directories and files like package.json, tsconfig.json, etc.
};
```

### 2. Updating `TEMPLATES.json`

After creating your template folder and `files.ts`, you need to add an entry for your template in the `TEMPLATES.json` file at the root of this repository. This file acts as a manifest for all available templates, providing metadata that will be displayed in the IDE.

The structure for each entry in `TEMPLATES.json` is as follows:

```json
{
    "your_template_slug": {
        "name": "Your Template Name",
        "desc": "A brief description of what your contract does.",
        "level": "Beginner", // or "Intermediate", "Advanced"
        "lang": "Pyteal" // or "TealScript"
    }
}
```

**Example:**

For a `hello_world` template, the `TEMPLATES.json` entry would look like this:

```json
{
    "hello_world": {
        "name": "Hello World",
        "desc": "A simple hello world program with PyTeal/Python.",
        "level": "Beginner",
        "lang": "Pyteal"
    }
}
```

Please ensure that the `slug_name` in `TEMPLATES.json` exactly matches the folder name you created in `playground/`.

### 3. Submitting Your Contribution

Once you have created your template folder, `files.ts`, and updated `TEMPLATES.json`, please submit a Pull Request (PR) to this repository. I will review your contribution and merge it if it meets the guidelines.

Thank you for contributing to the Algorand developer community!
