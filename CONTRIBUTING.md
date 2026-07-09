# Contributing Guide

Thank you for your interest in contributing to the Quotation Builder! This guide will help you understand the project structure and how to contribute.

## Code of Conduct

- Be respectful and inclusive
- Provide constructive feedback
- Help others learn and grow

## How to Contribute

### 1. Report a Bug

Found a bug? [Open an issue](../../issues) with:
- Clear title describing the bug
- Steps to reproduce
- Expected vs. actual behavior
- Screenshots if applicable
- Your environment (browser, OS, etc.)

### 2. Request a Feature

Have an idea? [Open an issue](../../issues) with:
- Clear feature description
- Why it would be useful
- Potential implementation approach
- Examples from other tools (if applicable)

### 3. Submit Code Changes

#### Setup Development Environment
```bash
# Clone repository
git clone https://github.com/yourusername/quotation-builder.git
cd quotation-builder

# Install dependencies
npm install

# Start development server
npm run dev

# In another terminal, run linter
npm run lint
```

#### Make Your Changes
1. Create a feature branch
   ```bash
   git checkout -b feature/your-feature-name
   ```

2. Follow coding standards
   - Use React Hooks (no class components)
   - Keep components small and focused
   - Write clear variable names
   - Add comments for complex logic

3. Test your changes
   - Manual testing in browser
   - Test on multiple browsers/devices
   - Verify PDF generation works
   - Check mobile responsiveness

4. Run linter
   ```bash
   npm run lint
   ```

5. Commit with clear messages
   ```bash
   git commit -m "Add feature: clear description of change"
   ```

6. Push to your fork
   ```bash
   git push origin feature/your-feature-name
   ```

7. Create Pull Request
   - Clear title and description
   - Reference any related issues
   - Explain the changes and why

### 4. Improve Documentation

Documentation improvements are always welcome:
- Fix typos or clarify instructions
- Add examples or use cases
- Translate docs to other languages
- Create tutorials or guides

## Project Structure

```
src/
├── components/
│   ├── Intake/           # Client information forms
│   ├── ServiceSelection/ # Service selection modals
│   ├── QuotationSummary/# Service list & pricing
│   └── PDFTemplate/      # PDF generation
├── hooks/                # React custom hooks
├── utils/                # Helper functions
├── config/               # Configuration files
└── App.jsx               # Main component
```

## Key Areas for Contribution

### High Priority
- [ ] Multi-language support (i18n)
- [ ] Additional PDF design themes
- [ ] Service templates library
- [ ] Quotation history/archiving

### Medium Priority
- [ ] WhatsApp integration
- [ ] Email quotation sending
- [ ] Client approval workflow
- [ ] Advanced analytics

### Low Priority (Nice to Have)
- [ ] Dark mode
- [ ] Service photos gallery
- [ ] Payment gateway integration
- [ ] CRM integration

## Coding Standards

### Component Structure
```jsx
// Use named exports
export const ComponentName = ({ prop1, prop2 }) => {
  // Component logic
  return (
    <div>
      {/* JSX */}
    </div>
  )
}
```

### Naming Conventions
- Components: `PascalCase` (ComponentName.jsx)
- Functions: `camelCase` (handleClick, calculateTotal)
- Constants: `UPPER_SNAKE_CASE` (MAX_ITEMS)
- CSS classes: `kebab-case` (service-item, primary-button)

### Comments
```javascript
// Use comments for WHY, not WHAT
// Good: Calculate subtotal including all discounts
const subtotal = items.reduce((sum, item) => sum + item.price, 0)

// Bad: Add up the prices
const subtotal = items.reduce((sum, item) => sum + item.price, 0)
```

## Pull Request Process

1. **Before submitting:**
   - Rebase with main branch
   - Run tests and linter
   - Update documentation if needed
   - Add comments to complex code

2. **PR Description Should Include:**
   - Clear title
   - What changes were made
   - Why the change is needed
   - How to test the changes
   - Any breaking changes

3. **Review Process:**
   - Maintainers will review your code
   - Be open to feedback
   - Make requested changes promptly
   - Respond to comments

4. **Merge:**
   - PR must pass all checks
   - At least one approval required
   - Your contribution is merged!

## Testing

### Manual Testing
```bash
npm run dev
# Test in browser at http://localhost:3000
# Test all user flows
# Test on mobile
# Verify PDF generation
```

### Automated Testing (When Available)
```bash
npm run test
```

## Git Commit Messages

- Use present tense ("Add feature" not "Added feature")
- Use imperative mood ("Move cursor" not "Moves cursor")
- Limit first line to 72 characters
- Reference issues when applicable

Examples:
```
Add bridal event customization
Fix PDF generation on Safari
Update business config structure
Remove deprecated service option
```

## Release Process

Maintainers follow semantic versioning:
- **v1.0.0** → Major version (breaking changes)
- **v1.1.0** → Minor version (new features)
- **v1.0.1** → Patch version (bug fixes)

## Questions?

- Check existing issues and discussions
- Review documentation and planning docs
- Ask in issue comments
- Open a discussion thread

## License

By contributing, you agree that your contributions will be licensed under the same MIT License as the project.

---

**Thank you for contributing to the Quotation Builder! Your efforts help makeup artists worldwide.** ❤️
