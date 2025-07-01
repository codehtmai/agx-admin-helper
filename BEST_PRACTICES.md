# Recommended Updates and Best Practices

This project is based on a boilerplate for building Chrome extensions with React and Webpack. To keep the extension up to date and maintainable, consider the following improvements:

## Keep Dependencies Current

- **React 18** and **React DOM 18** are now stable. Upgrading allows the use of hooks like `useId` and concurrent features. Update the related `@types` packages as well.
- Update Webpack, TypeScript, and `@types/chrome` to the latest versions for better performance and support for Manifest V3 APIs.
- Replace deprecated packages (`react-hot-loader`, `node-sass`) with modern alternatives such as **React Refresh** and **sass**.

## Manifest Best Practices

- Limit `content_scripts.matches` and `host_permissions` to the URLs your extension actually needs. Avoid `<all_urls>` unless absolutely necessary.
- Use the `action` key (rather than `browser_action` or `page_action`) and supply appropriate `default_icon` and `default_title` values.
- Include a `description`, `version`, and, if possible, a `minimum_chrome_version` to clarify compatibility.
- Consider using ES module syntax in your service worker (`background.service_worker`) for better tree shaking and future compatibility.

## Code Quality

- Enforce consistent formatting with Prettier and linting with ESLint. Add an `npm` script such as `npm run lint` and run it in CI or as a pre-commit hook with a tool like **husky**.
- Adopt TypeScript across all source files for type safety. Convert remaining `.js` files in `src` to `.ts` or `.tsx` and enable `strict` mode in `tsconfig.json`.

## Performance and Security

- Use the `chrome.scripting` API instead of the older `executeScript` where possible. This is the recommended approach for Manifest V3.
- Keep your content scripts lightweight and, if needed, load code dynamically using `import()` to reduce initial payload size.
- Audit the extension for unnecessary permissions and remove any that are not required.

## Testing and Documentation

- Add unit and integration tests for critical logic using a framework like **Jest** and **React Testing Library**. This helps catch regressions and improves maintainability.
- Document build and release steps in the README, including how to create a production bundle with `npm run build` and how to load the unpacked extension in Chrome.

For more details on the latest guidelines, see the [Chrome extension developer documentation](https://developer.chrome.com/docs/extensions/).
