---
title: "splitit"
description: "A bill tracking, organisation, and payment solution for multiple users."
summary: "A bill tracking, organisation, and payment solution for multiple users."
weight: 30
---

[Check it out on GitHub here!](https://github.com/theranos2/SplitIt/)

# Setting up development environment
- Ensure dotnet 5.0 SDK is installed
- Run `make init`, it executes:
    - `dotnet restore` to restore all project dependencies
    - `dotnet tool restore` to restore tools used for the project
    - Install `pre-commit` tool using `pip` and setup pre-commit hooks
- Ensure the latest LTS node version is installed (v16.15.1)
    - Use [nvm](https://github.com/nvm-sh/nvm) to make your life easier

# Using swagger with authenticated routes
- Click 'Authorize 🔒' on the top right of the page
- Paste your token and click 'Authorize'
- Now all requests you send will have the `Token` header

# Database migrations
- Currently not in use
- Ensuring schema changes are reflected in database:
```
rm -rf Migrations/
rm -f database.db
dotnet ef migrations add "Initial" && dotnet ef database update 
```
- Or just run `make db-reset`

# Using Http Exceptions
```c#
using split_it.Exceptions.Http;

// On error
throw new HttpBadRequest("Reason");
throw new HttpInternalServer("Reason");
throw new HttpNotFound("Reason");
```
- Refer code to see all possible overloads

# Using typescript client
## Generating from source
- Ensure dotnet server is running (`dotnet run`)
- In `src` directory do: `make typescript-client` (need java installed)
- Do not modify any of the files generated in `src/ClientApp/src/api`
## Consuming generated client
```tsx
import { UserApi } from 'api';
const someFunc = async () => {
  const api = new UserApi({ apiKey: "Token From Context" });
  const result = await api.apiUserGet();
}
```
- Refer `src/ClientApp/src/api` for more ways to use the generated client