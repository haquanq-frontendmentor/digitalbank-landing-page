<script lang="ts">
  import { ConfettiImage, CurrencyImage, PlaneImage, RestaurantImage } from "../assets/images";
  import Container from "../layouts/Container.svelte";
  import Paragraph from "./common/Paragraph.svelte";
</script>

{#snippet Article(image: string, author: string, title: string, description: string)}
  <li class="max-w-120 overflow-hidden rounded-sm bg-white shadow-sm">
    <img class="h-50 w-full object-cover object-center" src={image} alt="" />
    <div class="px-5 pt-6 pb-[1.8125rem]">
      <span class="mb-4 block text-[0.625rem] leading-[0.6875rem]">{author}</span>
      <h3 class="mb-2 text-base leading-[1.1875rem] font-normal md:tracking-[-0.02em]">
        <a class="transition-colors hover:text-cyan-400" href="">{title}</a>
      </h3>
      <Paragraph>{description}</Paragraph>
    </div>
  </li>
{/snippet}

<section>
  <Container>
    <div class="py-16 md:py-[5.1875rem]">
      <h2 class="mb-12 text-center text-[2rem] leading-10 md:mb-14 md:text-[2.5rem] md:leading-12 lg:text-start">
        Latest Articles
      </h2>
      <ul class="grid justify-center gap-8 md:grid-cols-2 lg:grid-cols-4">
        {@render Article(
          CurrencyImage,
          "By Claire Robinson",
          "Receive money in any currency with no fees",
          "The world is getting smaller and we’re becoming more mobile. So why should you be forced to only receive money in a single …",
        )}
        {@render Article(
          RestaurantImage,
          "By Wilson Hutton",
          "Treat yourself without worrying about money",
          "Our simple budgeting feature allows you to separate out your spending and set realistic limits each month. That means you …",
        )}
        {@render Article(
          PlaneImage,
          "By Wilson Hutton",
          "Take your Digitalbank card wherever you go",
          "We want you to enjoy your travels. This is why we don’t charge any fees on purchases while you’re abroad. We’ll even ...",
        )}
        {@render Article(
          ConfettiImage,
          "By Claire Robinson",
          "Our invite-only Beta accounts are now live!",
          "After a lot of hard work by the whole team, we’re excited to launch our closed beta. It’s easy to request an invite through ...",
        )}
      </ul>
    </div>
  </Container>
</section>
