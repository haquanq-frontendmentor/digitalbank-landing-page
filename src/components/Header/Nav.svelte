<script lang="ts">
  import type { Action } from "svelte/action";
  import { cn } from "../../utils/cn";

  let menuOpening = $state(false);

  const buttonAction: Action<HTMLButtonElement> = (button) => {
    button.addEventListener("click", (e) => {
      e.stopPropagation;
      menuOpening = !menuOpening;
    });

    window.addEventListener("resize", (e) => {
      if (window.matchMedia("(min-width: 48em)").matches) {
        if (menuOpening) menuOpening = false;
      }
    });
  };

  const backgroundAction: Action<HTMLElement> = (element) => {
    element.addEventListener("click", () => {
      menuOpening = false;
    });
  };

  const navListAction: Action<HTMLElement> = (element) => {
    element.addEventListener("click", (e) => {
      e.stopPropagation();
    });

    element.addEventListener("keydown", (e) => {
      if (!e.shiftKey && e.key === "Escape") {
        menuOpening = false;
      }
    });

    const focusableElements = element.querySelectorAll("a") as NodeListOf<HTMLAnchorElement>;

    focusableElements[0].addEventListener("keydown", (e) => {
      if (e.shiftKey && e.key === "Tab" && menuOpening) {
        requestAnimationFrame(() => {
          focusableElements[focusableElements.length - 1].focus();
        });
      }
    });

    focusableElements[focusableElements.length - 1].addEventListener("keydown", (e) => {
      if (!e.shiftKey && e.key === "Tab" && menuOpening) {
        requestAnimationFrame(() => {
          focusableElements[0].focus();
        });
      }
    });

    $effect(() => {
      if (menuOpening) {
        document.body.style.overflow = "hidden";
        window.scrollTo({ top: 0, behavior: "smooth" });
        focusableElements[0].focus();
      } else {
        document.body.style.overflow = "";
      }
    });
  };
</script>

<nav class="" aria-label="Header navigation">
  <button
    class="group relative z-100 flex h-[1.375rem] flex-col items-center justify-center *:h-[0.125rem] *:w-6 *:bg-blue-950 md:hidden"
    type="button"
    aria-label="Mobile menu"
    aria-controls="mobile-menu"
    aria-expanded={menuOpening}
    use:buttonAction
  >
    <span class="transition-transform group-aria-expanded:rotate-45"></span>
    <span class="my-[0.1875rem] group-aria-expanded:hidden"></span>
    <span class="transition-transform group-aria-expanded:-mt-[0.125rem] group-aria-expanded:-rotate-45"></span>
  </button>

  <div
    class={cn(
      "absolute inset-x-0 top-full z-50 hidden h-[calc(100vh-100%)] [background:var(--gradient-backdrop)] md:static md:inset-0 md:block md:h-20 md:pl-[0.0625rem] md:[background:initial]",
      menuOpening && "block",
    )}
    id="mobile-menu"
    use:backgroundAction
  >
    <ul
      class="mx-auto mt-6 flex w-[min(100vw-3rem,25rem)] flex-col items-center gap-6 rounded-sm bg-white py-8 text-lg leading-5 text-blue-950 md:m-0 md:h-full md:w-auto md:flex-row md:gap-8 md:bg-transparent md:p-0 md:text-sm md:leading-4"
      use:navListAction
    >
      {#snippet NavItem(title: string)}
        <li class="relative flex items-center md:h-full">
          <a
            class="block transition-colors md:text-gray-800 md:after:pointer-events-none md:after:absolute md:after:bottom-0 md:after:left-0 md:after:h-1 md:after:w-full md:after:opacity-0 md:after:transition-opacity md:after:[background:var(--gradient-green)] md:hover:text-blue-950 md:hover:after:opacity-100"
            href="">{title}</a
          >
        </li>
      {/snippet}
      {@render NavItem("Home")}
      {@render NavItem("About")}
      {@render NavItem("Contect")}
      {@render NavItem("Blog")}
      {@render NavItem("Careers")}
    </ul>
  </div>
</nav>
