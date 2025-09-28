<script>
  import { LogoLight } from "../../assets/images";
  import Container from "../../layouts/Container.svelte";
  import Button from "../common/Button.svelte";
  import FooterNav from "./FooterNav.svelte";
  import FooterSocials from "./FooterSocials.svelte";
</script>

<footer class="bg-blue-950">
  <Container>
    <div
      class="grid gap-x-6 gap-y-8 px-[0.1875rem] py-[3.375rem] *:justify-self-center md:grid-cols-3 md:*:justify-self-start lg:grid-cols-4 lg:pt-[2.9375rem] lg:pb-[2.875rem]"
    >
      <div class="flex flex-col gap-8 md:justify-between">
        <a href="" aria-label="Homepage">
          <img src={LogoLight} alt="" />
        </a>
        <FooterSocials />
      </div>
      <div class="w-[17.6875rem] lg:col-span-2">
        <FooterNav />
      </div>
      <div class="flex w-full flex-col items-center gap-6 md:col-start-3 md:items-end lg:col-start-4">
        <Button>Request Invite</Button>
        <p class="shrink-0 text-sm leading-4">© Digitalbank. All Rights Reserved</p>
      </div>
    </div>
  </Container>
</footer>
