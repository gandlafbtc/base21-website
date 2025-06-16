<script lang="ts">
	import { t_comming_soon } from '$lib/paraglide/messages';
  import { onMount } from 'svelte';
  
  // For animated typing effect
  let currentTextIndex = 0;
  let displayText = '';
  let isDeleting = false;
  let typingSpeed = 100;
  let pauseDelay = 3000;
  let pauseDelay2 = 300;
  
  const textArray = [
    'Freedom Tech',
    'Coworking',
    'Community',
    'Open Source',
  ];
  
  function typeEffect() {
    const currentText = textArray[currentTextIndex];
    
    if (isDeleting) {
      displayText = currentText.substring(0, displayText.length - 1);
    } else {
      displayText = currentText.substring(0, displayText.length + 1);
    }
    
    // Set typing speed
    let typeSpeed = isDeleting ? typingSpeed / 2 : typingSpeed;
    
    // If complete word is typed
    if (!isDeleting && displayText === currentText) {
      typeSpeed = pauseDelay;
      isDeleting = true;
    } else if (isDeleting && displayText === '') {
      typeSpeed = pauseDelay2;
      isDeleting = false;
      currentTextIndex = (currentTextIndex + 1) % textArray.length;
    }
    
    setTimeout(typeEffect, typeSpeed);
  }
  
  onMount(() => {
    typeEffect();
  });
</script>

<svelte:head>
  <title> BASE21 | Technology & Coworking </title>
  <meta name="description" content="Base21 is a research and development startup focused on Bitcoin, Chaumian ecash, and cryptographic blinding schemes." />
</svelte:head>

<div class="min-h-screen bg-base-300">
  <!-- Hero Section -->
  <div class="hero min-h-screen bg-base-300">
    <div class="hero-content text-center">
      <div class="max-w-4xl">
        <img src="/base21-white.svg" alt="Base21 Logo" class="w-96"/>
        <div class="py-6 text-2xl flex gap-0.5">
          <span class="font-bold styled-font  text-primary min-h-[2.5rem] inline-block">{displayText}</span>
          <div class="animate-pulse bg-primary w-1 h-7"></div>
        </div>
        <p class="py-6 text-lg text-base-content/70 max-w-3xl mx-auto">
          {t_comming_soon()}
          <!-- Research, Development,  Coworking. -->
        </p>
        <!-- <div class="flex flex-wrap justify-center gap-4">
          <button class="btn btn-primary">Coworking space</button>
          <button class="btn btn-outline btn-primary">Research</button>
        </div> -->
        <a class="btn btn-primary rounded-full" href="mailto:info@base21.tech">
          info@base21.tech
        </a>
      </div>
    </div>
  </div>
</div>
