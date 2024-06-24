## Frontend Mentor Challenge 14 - Workit Landing Page

This is my solution to the [Workit Landing Page](https://www.frontendmentor.io/challenges/workit-landing-page-2fYnyle5lu) challenge on [Frontend Mentor](https://www.frontendmentor.io/).

### Screenshots of My Solution (Desktop & Mobile). 🔍

![](./solution_screenshots/screenshot_desktop.jpeg)
![](./solution_screenshots/screenshot_mobile.jpeg)

#

### Links. 🔗

- Live Site URL: https://workit-landing-page-darkstarxdd.vercel.app/

#

### Built with. 🔨

- HTML & CSS.
- Vite.

#

### Features. ✨

- Used a **`<picture>`** element to serve a more optimized hero image for the mobile and tablet screen sizes.
- Included a visually hidden heading to improve accessibility for screen reader users.
- Self-hosted fonts for faster loading.

#

### Testing and Accessibility. 🧪

- Used the Responsively App to check how the site looks on various screen sizes, starting from 320 x 480 and going up to 3000 x 2000.
- Using Firefox on desktop, changed the browser font size to extreme low and high values (9px to 56px respectively).
- Zoom the page in and out using Ctrl + Scroll wheel.
- Tested using NVDA screen reader.
- Viewed the site on an iPhone 11.
- Performed Lighthouse and PageSpeed tests. ([PageSpeed Result.](https://pagespeed.web.dev/analysis/https-workit-landing-page-darkstarxdd-vercel-app/7ylu6a0i49?form_factor=mobile))

#

### New Things Learned. 🎓

- Some new properties related to **`text-decoration`**.

  ```css
  .hero__title em {
    font-style: normal;
    text-decoration: underline;
    text-decoration-color: var(--clr-primary-400);
    text-decoration-thickness: 0.1875rem;
    text-underline-offset: 0.5rem;
  }
  ```

#

### Problems Faced. 🚧

- I wanted to use `overflow-x: hidden` on the `.main` element to hide the horizontal overflow of the green background patterns at the top of the page. However, when I added `overflow-x: hidden`, a scrollbar appeared in the **_vertical_** direction. This was very confusing to me. Turns out, [if you set overflow-x to hidden, overflow-y is automatically set to auto](https://stackoverflow.com/a/6433475). That’s why I was getting a vertical scrollbar even though I was dealing with the horizontal axis using `overflow-x: hidden`. This was an issue since I wanted the top green patterns’ horizontal overflow to be hidden while allowing the bottom green background patterns’ vertical overflow to be fully visible.

  - The solution was, instead of using `overflow-x: hidden`, use `overflow-x: clip`. When [clip](https://kilianvalkhof.com/2022/css-html/do-you-know-about-overflow-clip/) is used, it allows you to clip the overflowing content in one direction (in my case it was horizontal), while keeping your overflowing content on another direction (vertical for me) still visible.

- I have the green background patterns absolutely positioned as pseudo elements of the `.main`. Initially I used the `url()` inside the `content` property to reference the image path.

  ```css
  .main:after {
    content: url("/assets/bg-pattern-3.svg");
    position: absolute;
    width: 11rem;
    height: 11rem;
    bottom: -26.5rem;
    right: 1rem;
  }
  ```

  While this was working, this had an issue. When the browser font size was changed, the image did not scale with the browser and as a result they would go out of position. Text content inside the `content` property does scale with the browser font size. So I assumed image content would too. But for some reason they don’t.

  - The fix was to reference the image using the `background-image` property instead of doing that inside the `content` property. Now those green patterns scale up and down when the browser font size is changed.

    ```css
    .main::after {
      content: "";
      position: absolute;
      width: 10.875rem;
      height: 11.15rem;
      background-image: url("/assets/images/bg-pattern-2.svg");
      background-size: contain;
      background-repeat: no-repeat;
      top: 9.5rem;
      right: -6rem;
    }
    ```

#

### Ending Notes. 📝

- I used to include both WOFF2 and WOFF font files, but seems like WOFF2 is fully supported by all major browsers, so I am gonna stop including the WOFF file type as a fallback option.
- Changed my `<head>` section boilerplate in this project. Did some tweaks to the order I used to place the tags inside the `<head>` section. Moving forward will be using that.
- Initially, I used `border-radius` to create the curved background colors on the page. While this method gave a good result, it was bit hard to get the exact curve given in the design. So later I used an SVG instead.

  ```css
  border-bottom-left-radius: 50% 4%;
  border-bottom-right-radius: 50% 4%;
  ```

- There was one issue I could not find a way to fix.
  - When viewed on mobile there is a 1px gap that appears between the top two sections. I can’t see that gap when viewed using dev tools, but when viewed on an actual mobile device, it’s present. This is probably because the way I have implemented the hero sections’ curved background.

#

### Tools I Use. 🔧

- [Prettier VS Code Extension](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) - Code formatter.

- [Responsively.app](https://responsively.app/) - A free and open source tool that allows you to test your webpage on different screen sizes, take screenshots and much more.

- [Color Contrast Checker by coolors.co](https://coolors.co/contrast-checker/112a46-acc8e5) - Check color contrast ratios and if needed, update the colors to match the WCAG guidelines.

- [Google Webfonts Helper by Mario Ranftl](https://gwfh.mranftl.com/fonts) - Provides WOFF2 format for Google Fonts.

- [PerfectPixel by WellDoneCode](https://chromewebstore.google.com/detail/perfectpixel-by-welldonec/dkaagdgjmgdmbnecmcefdhjekcoceebi) - A chrome extension that enables you to overlay an image, over a webpage. This makes it easier to compare your solution result with the reference image and adjust fine details if needed.

#

- My Frontend Mentor Profile - [@DarkstarXDD](https://www.frontendmentor.io/profile/DarkstarXDD)
