<script>
	import { page } from '$app/state';
  import { onMount } from 'svelte';
	import { setLocale } from './paraglide/runtime';
  
  let scrolled = false;
  
  onMount(() => {
    const handleScroll = () => {
      scrolled = window.scrollY > 10;
    };
    
    // Initial check
    handleScroll();
    
    // Add event listener
    window.addEventListener('scroll', handleScroll);
    
    // Clean up
    return () => {
      window.removeEventListener('scroll', handleScroll);
    };
  });
</script>

<div class="navbar h-12 fixed z-50 transition-all duration-300 {scrolled ? 'bg-base-100 shadow-sm' : 'bg-transparent'}">

    <div class="flex-1">
      <a href="/">
        <img src="/base21-white.svg" alt="Base21 Logo" class="w-36"/>
    </a>
    </div>
    <div>
        <div>
          <button class="btn btn-ghost btn-circle" onclick={()=>setLocale("en")}>
            <img src="/uk.svg" alt="english" class="w-5">
          </button>
          <button class="btn btn-ghost btn-circle" onclick={()=>setLocale("kr")}>
            <img src="/kr.svg" alt="korean" class="w-5">
          </button>
        </div>
    </div>
    <!-- <div class="dropdown dropdown-bottom dropdown-left">
        <div tabindex="0" role="button" class="btn btn-ghost btn-circle">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor"> <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h7" /> </svg>
        </div>
        <ul
          tabindex="0"
          class="menu menu-sm dropdown-content bg-base-100 rounded-box z-1 mt-3 w-52 p-2 shadow">
          <li><a>Home</a></li>
          <li><a>About</a></li>
        </ul>
      </div> -->
  </div>
