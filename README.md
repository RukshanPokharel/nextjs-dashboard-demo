# nextjs-dashboard-demo

A practice project to learn nextjs

#Notes taken while devloping the webapp

## Next.js downloads font files at build time and hosts them with your other static assets. This means when a user visits your application, there are no additional network requests for fonts which would impact performance.

## Images without dimensions and web fonts are common causes of layout shift due to the browser having to download additional resources.

    -- adding image in next js
    1. import Image from "next/image";
    2. <Image
            src={"/hero-desktop.png"}
            width={1000}
            height={760}
            className="hidden md:block"
            alt="Screenshots of the dashboard project showing desktop version"
     ></Image>

## One benefit of using layouts in Next.js is that on navigation, only the page components update while the layout won't re-render. This is called partial rendering.

## Any UI you add to the root layout will be shared across all pages in your application. You can use the root layout to modify your <html> and <body> tags, and add metadata.

What is the purpose of the layout file in Next.js?
ans:- To share UI across multiple pages. The layout file is the best way to create a shared layout that all pages in your application can use.

## The Link component is similar to using <a> tags, but instead of <a href="…">, you use <Link href="…">. using <a> (anchor tag) for navigation refreshes the whole page so we replace <a> with <Link/> component from next/link to navigate and not refresh the page.

(

## Automatic code-splitting and prefetching

To improve the navigation experience, Next.js automatically code splits your application by route segments. This is different from a traditional React SPA, where the browser loads all your application code on initial load.

Splitting code by routes means that pages become isolated. If a certain page throws an error, the rest of the application will still work.

Furthermore, in production, whenever <Link> components appear in the browser's viewport, Next.js automatically prefetches the code for the linked route in the background. By the time the user clicks the link, the code for the destination page will already be loaded in the background, and this is what makes the page transition near-instant!
)

What does Next.js do when a <Link> component appears in the browser’s viewport in a production environment?
ans:- Prefetches the code for the linked route.

What is one advantage of streaming?
ans:- Chunks(or components) are rendered in parallel, reducing the overall load time. One advantage of this approach is that you can significantly reduce your page's overall loading time.

# defaultValue vs. value / Controlled vs. Uncontrolled

If you're using state to manage the value of an input, you'd use the value attribute to make it a controlled component. This means React would manage the input's state.
However, since you're not using state, you can use defaultValue. This means the native input will manage its own state. This is okay since you're saving the search query to the URL instead of state.

What problem does debouncing solve in the search feature?
ans:- It prevents a new database query on every keystroke, thus saving resources.

# By adding the 'use server', you mark all the exported functions within the file as Server Actions. These server functions can then be imported and used in Client and Server components.

You can also write Server Actions directly inside Server Components by adding "use server" inside the action.

# Good to know: In HTML, you'd pass a URL to the action attribute. This URL would be the destination where your form data should be submitted (usually an API endpoint).

However, in React, the action attribute is considered a special prop - meaning React builds on top of it to allow actions to be invoked. Behind the scenes, Server Actions create a POST API endpoint. This is why you don't need to create API endpoints manually when using Server Actions.

# Tip: If you're working with forms that have many fields, you may want to consider using the entries() method with JavaScript's Object.fromEntries(). For example:

const rawFormData = Object.fromEntries(formData.entries())

# UUIDs vs. Auto-incrementing Keys

We use UUIDs instead of incrementing keys (e.g., 1, 2, 3, etc.). This makes the URL longer; however, UUIDs eliminate the risk of ID collision, are globally unique, and reduce the risk of enumeration attacks - making them ideal for large databases. However, if you prefer cleaner URLs, you might prefer to use auto-incrementing keys.

# What's one benefit of using a Server Actions?

Progressive Enhancement. This allows users to interact with the form and submit data even if the JavaScript for the form hasn't been loaded yet or if it fails to load.

# Which file in Next.js serves as a catch-all for unexpected errors in your route segments?

error.tsx. The `error.tsx` file serves as a catch-all for unexpected errors and allows you to display a fallback UI to your users.

# Accessibility in a web app?

Accessibility refers to designing and implementing web applications that everyone can use, including those with disabilities. It's a vast topic that covers many areas, such as keyboard navigation, semantic HTML, images, colors, videos, etc.

# Authentication verifies your identity. Authorization determines what you can access.

# The advantage of employing Middleware for auth

The protected routes will not even start rendering until the Middleware verifies the authentication, enhancing both the security and performance of your application.
