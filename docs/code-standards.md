# Code Standards

These standards help keep the Mara Guard codebase consistent, readable, and maintainable across the web, backend, mobile, and IoT components.

<div style="height: 1px; background-color: rgba(255, 255, 255, 0.15); margin: 24px 0;"></div>

## General Principles

* **Readability:** Use clear and descriptive names for variables, functions, classes, and components.
* **Keep it simple:** Prefer simple solutions over unnecessary complexity.
* **Don't repeat yourself:** Reuse existing functions, components, and utilities where appropriate.
* **Consistency:** Follow the conventions already established in the repository you are working on.

<div style="height: 1px; background-color: rgba(255, 255, 255, 0.15); margin: 24px 0;"></div>

## Naming Conventions

Use naming conventions appropriate to the technology:

* **JavaScript:** Use `camelCase` for variables and functions and `PascalCase` for components and classes.
* **Python:** Use `snake_case` for variables and functions.
* **Dart / Flutter:** Follow Dart naming conventions, including `camelCase` for variables and functions and `PascalCase` for classes and widgets.
* **Files:** Follow the naming convention already established in the relevant repository. Do not introduce a different naming style within the same project.

<div style="height: 1px; background-color: rgba(255, 255, 255, 0.15); margin: 24px 0;"></div>

## Code Formatting and Linting

Use the formatting and linting tools configured in each repository.

Before creating a Pull Request:

* Run the project's available linting checks.
* Format code according to the project's configuration.
* Resolve linting and formatting errors before submitting the Pull Request.

<div style="height: 1px; background-color: rgba(255, 255, 255, 0.15); margin: 15px 0;"></div>

## Comments and Documentation

* Write comments only when they help explain complex or non-obvious logic.
* Keep comments short and relevant.
* Update comments when the related code changes.
* Use clear documentation for functions, classes, APIs, and other reusable components where required.

<div style="height: 1px; background-color: rgba(255, 255, 255, 0.15); margin: 24px 0;"></div>

## Error Handling

* Handle errors where they can occur.
* Provide clear and useful error messages.
* Avoid exposing sensitive information in error responses or logs.
* Do not silently ignore errors.

<div style="height: 1px; background-color: rgba(255, 255, 255, 0.15); margin: 24px 0;"></div>

## Git Workflow

* Create a separate branch for each feature, fix, or documentation change.
* Use clear and descriptive branch names.
* Keep commits focused on a single change.
* Write meaningful commit messages.
* Pull Requests should describe the changes made and include relevant testing information.

<div style="height: 1px; background-color: rgba(255, 255, 255, 0.15); margin: 24px 0;"></div>

## Testing

Code changes should be tested before submitting a Pull Request.

The project uses:

* **Postman** for API testing.
* **Cypress** for end-to-end testing.
* **Playwright** for automated application testing.
