<script lang="ts">
  import { ApiIcon, BudgetingIcon, OnboardingIcon, OnlineIcon } from "../assets/images";
  import Container from "../layouts/Container.svelte";
  import Paragraph from "./common/Paragraph.svelte";
</script>

{#snippet Feature(icon: string, title: string, description: string)}
  <li class="flex flex-col items-center lg:items-start">
    <img class="mb-10 aspect-square w-18" src={icon} alt="" />
    <h3 class="mb-6 text-2xl leading-7">{title}</h3>
    <Paragraph xClass="md:text-base max-w-100 md:leading-[1.625rem] tracking-[-0.014em]">{description}</Paragraph>
  </li>
{/snippet}

<section class="bg-gray-100">
  <Container>
    <div class="flex flex-col items-center py-16 text-center md:pt-24 md:pb-26 lg:items-start lg:text-start">
      <h2 class="mb-4 text-[2rem] leading-[2.375rem] md:mb-8 md:text-[2.5rem] md:leading-12">
        Why choose Digitalbank?
      </h2>
      <Paragraph xClass="mb-12 max-w-160 md:text-lg md:leading-7 md:mb-18 tracking-[-0.014em]">
        We leverage Open Banking to turn your bank account into your financial hub. Control your finances like never
        before.
      </Paragraph>

      <ul class="grid gap-8 md:grid-cols-2 lg:grid-cols-4">
        {@render Feature(
          OnlineIcon,
          "Online Banking",
          "Our modern web and mobile applications allow you to keep track of your finances wherever you are in the world.",
        )}
        {@render Feature(
          BudgetingIcon,
          "Simple Budgeting",
          "See exactly where your money goes each month. Receive notifications when you’re close to hitting your limits.",
        )}
        {@render Feature(
          OnboardingIcon,
          "Fast Onboarding",
          "We don’t do branches. Open your account in minutes online and start taking control of your finances right away.",
        )}
        {@render Feature(
          ApiIcon,
          "Open API",
          "Manage your savings, investments, pension, and much more from one account. Tracking your money has never been easier.",
        )}
      </ul>
    </div>
  </Container>
</section>
