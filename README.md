# TS-2: Responsive Landing Page with Tailwind CSS

## What This Is

This is a simple SaaS-style landing page I built to learn responsive design using Tailwind CSS v4. It has a sticky navbar, a hero section with a gradient background, feature cards, and a footer. The page works on phones, tablets, and desktops.

## How I Built It

I started with just the mobile layout since Tailwind is mobile-first. That was confusing at first because I kept thinking "write the desktop version, then shrink it down" but Tailwind works the opposite way — you write the small screen styles first and then add breakpoints like `md:` and `lg:` to change things on bigger screens.

The hardest part was the navbar. I wanted the links to show on desktop but hide on mobile and show a hamburger menu instead. I kept getting it wrong because I'd hide something with `hidden` and then forget that `md:flex` brings it back. Once I understood that the breakpoint class *overrides* the base class at that screen size, it clicked.

## Responsive Breakpoints I Used

- **`sm:` (640px)** — I used this for the footer so the copyright text sits next to the brand name instead of stacking
- **`md:` (768px)** — This is where the nav links appear, the hamburger hides, and the feature cards go from 1 column to 3 columns
- **`lg:` (1024px)** — The hero section switches from stacked (text on top, image below) to side-by-side

I picked these based on testing — on my phone things needed to stack, but on a tablet (around 768px) there was enough room for the nav links and 3-column grid.

## Tailwind Customization

I didn't just use the default Tailwind colors. In `input.css`, I set up custom theme tokens using `@theme` for brand colors, fonts, and spacing. I also created reusable component classes with `@layer components` (like `.btn-primary`) and a custom utility with `@layer utilities` (`.text-gradient`). This helped me understand how Tailwind's layer system works — utilities beat components beat base styles.

## The Hamburger Menu

I originally had an inline `onclick="..."` on the hamburger button. My instructor pointed out that mixing JS in the HTML like that is messy and hard to maintain. So I gave the button an `id` and used `addEventListener` in a script tag at the bottom. It does the same thing (toggles the `hidden` class on the mobile menu) but the code is cleaner and easier to debug.

## What I'd Do Differently

- Add smooth transitions when the mobile menu opens/closes instead of it just popping in
- Use a real logo image instead of just text
- Make the feature cards clickable with actual links
- Try adding a dark mode toggle since Tailwind has built-in dark mode support

## Tech Used

- HTML5
- Tailwind CSS v4
- Vanilla JavaScript (for the mobile menu toggle)