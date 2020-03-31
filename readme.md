- SSR for react

- Routing system. `pages/component.js` has a route `/component` generated. `[]` in the file name makes the dynamic routes, **`[]` should be the full name**.

- Webpack based for Hot reloading (showing syntax error instead of 500 if error)

- Link component for client-side navigation (not to use <a> because it will trigger a new request to the server)

- The only special folders are /pages and /public. Pages are for routings, and components can be everywhere.

- useRouter to get querystring

- use async function getInitialProps to fetch data. **It will only work to the default export component.** getInitialProps will only work on server side because we only need to fetch data once.

```js
Post.getInitialProps = async function (context) {
  console.warn('ax', { context });
  const { id } = context.query;
  const res = await fetch(`https://api.tvmaze.com/shows/${id}`);
  const show = await res.json();
  return { show };
}
```

- For a SPA: fetch on server side or client side: it depends on if the page is reloaded from server, or from a redirection from client side

- The css in js solution for them: https://github.com/zeit/styled-jsx. **Styles should go inside template strings.** **CSS rules have no effect on elements inside of a child component.**.