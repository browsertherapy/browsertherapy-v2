<script>
  import MainNav from './MainNav.svelte'
  import HamburgerMenuButton from './HamburgerMenuButton.svelte'
  import DarkModeButton from './DarkModeButton.svelte'
  import { siteTitle } from '$lib/config'

  const focusMain = () => {
		const main = document.querySelector('main');
		main.focus();
	}
</script>


<header>
  <a on:click|preventDefault={focusMain} class="skip-to-content-link" href="#main">
    Skip to main content
  </a>
  
  <a href="/" class="logo">
    <svg class="logo-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 243 213">
      <rect id="bt-window" x="1.5" y="1.5" width="240" height="210" rx="11.24" fill="#f4f7dc" stroke="#231f20" stroke-miterlimit="10" stroke-width="3"/>
      <path id="bt-heart" d="M310.64,206.13c-16-13.61-39.73-11.16-54.4,4L250.5,216l-5.74-5.91c-14.63-15.13-38.42-17.58-54.39-4a41.86,41.86,0,0,0-2.89,60.61L243.89,325a9.13,9.13,0,0,0,13.2,0l56.4-58.24a41.84,41.84,0,0,0-2.85-60.61Z" transform="translate(-128.42 -138.5)" fill="#f16668"/>
      <path id="bt-address-bg" d="M12.74,1.72H230.26A11.24,11.24,0,0,1,241.5,13V31.72a0,0,0,0,1,0,0H1.5a0,0,0,0,1,0,0V13A11.24,11.24,0,0,1,12.74,1.72Z" fill="#dcdc16" stroke="#231f20" stroke-miterlimit="10" stroke-width="2"/>
      <path id="bt-icon-bg" d="M305,170.22l-30-30h83.38a11.24,11.24,0,0,1,11.24,11.24v18.76Z" transform="translate(-128.42 -138.5)" fill="#99b33c" stroke="#231f20" stroke-miterlimit="10" stroke-width="2"/>
      <circle id="bt-icon-3" cx="186.3" cy="16.72" r="5" fill="#231f20"/>
      <circle id="bt-icon-2" cx="206.3" cy="16.72" r="5" fill="#231f20"/>
      <circle id="bt-icon-1" cx="226.3" cy="16.72" r="5" fill="#231f20"/>
    </svg>
    <span class="logo-browser">Browser</span>
    <span class="logo-therapy">Therapy</span>
  </a>
  
  <HamburgerMenuButton />
  <MainNav />

</header>