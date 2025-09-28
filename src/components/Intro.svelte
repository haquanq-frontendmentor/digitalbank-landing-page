<script>
  import { IntroPatternDesktop, IntroPatternMobile, MockupsImage } from "../assets/images";
  import Container from "../layouts/Container.svelte";
  import Button from "./common/Button.svelte";
  import Paragraph from "./common/Paragraph.svelte";
</script>

<section>
  <Container>
    <div class="grid justify-center md:grid-cols-[1fr_clamp(21.875rem,-1.1377rem+47.943vw,40.8125rem)] md:gap-6">
      <div class="relative md:col-start-2 md:w-auto md:*:pointer-events-none md:*:max-w-[500%]">
        <img
          class="absolute -inset-x-6 -top-14 w-[calc(100%+3rem)] max-w-[200%] md:hidden"
          src={IntroPatternMobile}
          alt=""
        />
        <img
          class="absolute hidden h-full w-[79.4375rem] object-cover object-[0_-16.1875rem] md:block"
          src={IntroPatternDesktop}
          alt=""
        />
        <img class="absolute -top-20 z-10 md:top-[-10.3125rem] md:left-[11.1875rem]" src={MockupsImage} alt="" />
      </div>
      <div
        class="col-start-1 flex flex-col items-center pt-[clamp(20.4375rem,-13.7347rem+145.8015vw,56.25rem)] pb-14 text-center md:row-start-1 md:items-start md:pt-[10.8125rem] md:pb-[10.8125rem] md:text-start"
      >
        <h1 class="mb-6 text-[2.5rem] leading-12 md:text-[3.5rem] md:leading-[4.1875rem]">
          Next generation digital banking
        </h1>
        <Paragraph xClass="mb-6 md:text-lg md:leading-7 md:tracking-[-0.014em]">
          Take your financial life online. Your Digitalbank account will be a one-stop-shop for spending, saving,
          budgeting, investing, and mu`ch more.
        </Paragraph>
        <Button link="">Request Invite</Button>
      </div>
    </div>
  </Container>
</section>
