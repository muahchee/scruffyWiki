React
========================
## Profiler component onRender function template

[docs](https://react.dev/reference/react/Profiler)

```
function onRender(
    id,
    phase,
    actualDuration,
    baseDuration,
    startTime,
    commitTime
  ) {
    console.log("id: " + id);
    console.log("phase: " + phase);
    console.log("actualDuration: " + actualDuration);
    console.log("baseDuration: " + baseDuration);
    console.log("startTime: " + startTime);
    console.log("commitTime: " + commitTime);
  }
  
  return (
    <Profiler id="ButtonComponent" onRender={onRender}>
       <ButtonComponent />
    </Profiler>
  );
```

---

## React Routing

### React-router URLs don't work when refreshing or writing manually

[explaination](https://stackoverflow.com/a/36623117)

> "So basically when you click a link, some JavaScript runs that manipulates the URL in the address bar, without causing a page refresh, which in turn causes React Router to perform a page transition on the client-side.
> 
> But now consider what happens if you copy-paste the URL in the address bar and e-mail it to a friend. Your friend has not loaded your website yet. In other words, she is still in phase 1. No React Router is running on her machine yet. So her browser will make a server request to http://example.com/about.
> 
> And this is where your trouble starts. Until now, you could get away with just placing a static HTML at the webroot of your server. But that would give 404 errors for all other URLs when requested from the server. Those same URLs work fine on the client-side, because there React Router is doing the routing for you, but they fail on the server-side unless you make your server understand them."

- neocities doesn't have redirect configuration.
    - [https://flamedfury.com/posts/a-simple-guide-to-redirects-on-neocities-with-eleventy/](https://flamedfury.com/posts/a-simple-guide-to-redirects-on-neocities-with-eleventy/)
    - When refreshing or directly going to a "sub-page" (e.g. `/games`), the server will go look for a `index.html `in a `games` folder - which doesn't exist.
- I'm currently using Uberspace, which is an Apache server
    - to configure redirects, just need to add a `.htaccess` file to the `public` folder

```
// --- public/.htaccess

RewriteBase /
RewriteRule ^index\.html$ - [L]
 RewriteCond %{REQUEST_FILENAME} !-f
 RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.html [L]
```
[https://ui.dev/react-router-cannot-get-url-refresh#apache-htaccess](https://ui.dev/react-router-cannot-get-url-refresh#apache-htaccess)

------

## routing for nginx

add to Vhost (in cloudpanel)

```
  location ~ "^/index\.html$" {
    break;
  }
  location / {
    try_files $uri $uri/ /index.html$is_args$args;
  }

```

[convert htaccess to nginx config] (https://www.getpagespeed.com/apache-to-nginx)

------


## Effects

[https://react.dev/learn/synchronizing-with-effects](https://react.dev/learn/synchronizing-with-effects)

> "Effects let you specify side effects that are caused by rendering itself, rather than by a particular event. 

Sending a message in the chat is an event because it is directly caused by the user clicking a specific button. 

However, setting up a server connection is an Effect because it should happen no matter which interaction caused the component to appear. 

Effects run at the end of a commit after the screen updates. This is a good time to synchronize the React components with some external system (like network or a third-party library)."

- Effects run after each render by default
- Effects run because of rendering. Rendering is caused by changes in state.
- Dependency Array
    - without - `useEffect` runs on every render
    - `[]` - `useEffect` only runs on mount (when the component appears)
    - `[a, b]` - `useEffect` runs on mount *and also* if either `a` or `b` have changed since the last render

-----
## Tips

- When something can be calculated from the existing props or state, don’t put it in state. Instead, calculate it during rendering.
- When you choose whether to put some logic into an event handler or an Effect, the main question you need to answer is what kind of logic it is from the user’s perspective. If this logic is caused by a particular interaction, keep it in the event handler. If it’s caused by the user seeing the component on the screen, keep it in the Effect.
