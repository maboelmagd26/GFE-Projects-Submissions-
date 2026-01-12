# Testimonial Card — Implementation Notes

## Overview

This project implements a small testimonial card using only HTML and vanilla CSS (no frameworks). The component is responsive and uses a flexbox layout for structure and a simple CSS truncation utility for long headings.

## Files / Structure

- index.html — main markup for the testimonial card
- css/style.css — all styling (layout, truncation, responsive rules)
- img/ — image assets used by the card (see "Responsive images" below)

## How it was built

1. Layout with Flexbox

   - The card wrapper uses a flex layout to align the profile thumbnail with the text content. This keeps the image and text aligned horizontally on wider screens and allows easy vertical stacking at narrow widths.

   Example (HTML skeleton):

   ```html
   <article class="testomnials-wrapper">
     <header>
       <figure>
         <img src="img/profile-thumbnail.png" alt="..." />
         <figcaption>
           <h3 class="truncate-long">
             Very long user name that needs truncation
           </h3>
           <p>@username</p>
         </figcaption>
       </figure>
     </header>
     <blockquote>
       <p>Testimonial text…</p>
     </blockquote>
   </article>
   ```

   Example (CSS concept):

   ```css
   .testomnials-wrapper {
     display: flex;
     gap: 1rem;
     align-items: flex-start;
   }
   figure {
     display: flex;
     gap: 0.75rem;
     align-items: center;
     margin: 0;
   }
   figcaption {
     display: flex;
     flex-direction: column;
   }
   ```

2. Truncation of the `h3` title

   - The `truncate-long` class uses the standard CSS ellipsis pattern to visually truncate overflowing text on a single line.

   CSS used:

   ```css
   .truncate-long {
     display: inline-block; /* or block depending on layout */
     max-width: 12rem; /* limit width so truncation can occur */
     white-space: nowrap; /* keep on one line */
     overflow: hidden; /* hide overflow */
     text-overflow: ellipsis; /* show "..." when truncated */
   }
   ```

3. Vanilla CSS only

   - All styles live in `css/style.css` and use no JavaScript or external CSS frameworks. Tailwind is linked in `index.html` for convenience but the component styling is plain CSS.

## Responsive images and breakpoints

To provide optimized imagery across breakpoints, use the `picture` element or `srcset` with widths. This repository includes placeholder images in `designs/` — add three sizes for the profile thumbnail (mobile, tablet, desktop). Example files:

- designs/Mobile.jpg
- designs/Tablet.jpg
- designs/Desktop.jpg

Recommended `picture` markup:

```html
<picture>
  <source media="(min-width:1440px)" srcset="designs/desktop.jpg" />
  <source media="(min-width:768px)" srcset="designs/tablet.jpg" />
  <img src="designs/mobile.jpg" alt="Profile thumbnail" />
</picture>
```

Suggested breakpoints (as used in the project):

- Mobile: up to 374px
- Tablet: 375px — 767px
- Desktop: 1440px and up

Example responsive CSS fragments:

```css
/* Mobile-first */
.testomnials-wrapper {
  display: block;
}

@media (min-width: 640px) {
  .testomnials-wrapper {
    display: flex;
  }
}

@media (min-width: 1024px) {
  .testomnials-wrapper {
    gap: 1.25rem;
  }
}
```

Built with HTML & vanilla CSS by [Maahmoud Aboelmagd](https://github.com/maboelmagd26) with the help of GFE Platform Projects challenges [Testomnial](https://www.greatfrontend.com/projects/challenges/testimonial-card/)
