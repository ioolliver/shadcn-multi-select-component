## Fork

This is a forked repository from [here](https://github.com/sersavan/shadcn-multi-select-component).

This repository have some improved features:

- MaxSelect
-> Allows you to set a maximum number of items a user can select. When this option is set, the (Select all) button will be disabled by default.

## Multi-Select Component Setup in Next.js

### Prerequisites

Ensure you have a Next.js project set up. If not, create one:

```bash
npx create-next-app my-app --typescript
cd my-app
```

### Step 1: Install shadcn Components

Install required shadcn components:

```bash
npx shadcn@latest init
npx shadcn@latest add command popover button separator badge
```

### Step 2: Create the Multi-Select Component

Create `multi-select.tsx` in your `components` directory and copy the code from the link below:

[Link to Component](https://github.com/ioolliver/shadcn-multi-select-component/blob/main/src/components/multi-select.tsx)

### Step 3: Integrate the Component

Update `page.tsx`:

```tsx
// src/app/page.tsx

"use client";

import React, { useState } from "react";
import { MultiSelect } from "@/components/multi-select";
import { Cat, Dog, Fish, Rabbit, Turtle } from "lucide-react";

const frameworksList = [
  { value: "react", label: "React", icon: Turtle },
  { value: "angular", label: "Angular", icon: Cat },
  { value: "vue", label: "Vue", icon: Dog },
  { value: "svelte", label: "Svelte", icon: Rabbit },
  { value: "ember", label: "Ember", icon: Fish },
];

function Home() {
  const [selectedFrameworks, setSelectedFrameworks] = useState<string[]>(["react", "angular"]);

  return (
    <div className="p-4 max-w-xl">
      <h1 className="text-2xl font-bold mb-4">Multi-Select Component</h1>
      <MultiSelect
        options={frameworksList}
        onValueChange={setSelectedFrameworks}
        defaultValue={selectedFrameworks}
        placeholder="Select frameworks"
        variant="inverted"
        animation={2}
        maxSelect={2}
        maxCount={3}
      />
      <div className="mt-4">
        <h2 className="text-xl font-semibold">Selected Frameworks:</h2>
        <ul className="list-disc list-inside">
          {selectedFrameworks.map((framework) => (
            <li key={framework}>{framework}</li>
          ))}
        </ul>
      </div>
    </div>
  );
}

export default Home;
```

### Step 4: Run Your Project

```bash
npm run dev
```
