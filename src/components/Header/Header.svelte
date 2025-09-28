<script>
  import { LogoDark } from "../../assets/images";
  import Container from "../../layouts/Container.svelte";
  import Button from "../common/Button.svelte";
  import Nav from "./Nav.svelte";
</script>

<header class="relative z-50 bg-white">
  <Container>
    <div class="flex items-center justify-between py-[1.3125rem] md:p-0 lg:px-[0.1875rem]">
      <a href="" aria-label="Homepage">
        <img src={LogoDark} alt="" />
      </a>
      <Nav />
      <Button xClass="hidden lg:block" link="">Request Invite</Button>
    </div>
  </Container>
</header>
