# Code Style Rules

## General Principles
- Write clear, readable code over clever code
- Follow existing patterns in the codebase
- Keep functions small and focused
- Use meaningful names

## Formatting
- Use project's configured formatter (Prettier, Black, etc.)
- Consistent indentation (spaces or tabs per project config)
- Max line length: 100 characters (configurable)

## Naming Conventions
- **Variables/functions**: camelCase (JS/TS) or snake_case (Python)
- **Classes/Components**: PascalCase
- **Constants**: UPPER_SNAKE_CASE
- **Files**: kebab-case or match framework convention

## Comments
- Comment *why*, not *what*
- Keep comments up to date with code
- Use JSDoc/docstrings for public APIs
- Remove commented-out code

## Error Handling
- Handle errors explicitly
- Provide meaningful error messages
- Log errors with context
- Never swallow errors silently

## Testing
- Write tests for new functionality
- Maintain existing test coverage
- Tests should be readable and maintainable
- Use descriptive test names

## Security
- Never commit secrets or credentials
- Validate all user input
- Use parameterized queries
- Follow OWASP guidelines
