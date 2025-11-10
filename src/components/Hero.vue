<script setup lang="ts">
import { useColorMode } from "@vueuse/core";

import { Button } from "@/components/ui/button";
import { ArrowRight } from "lucide-vue-next";
</script>

<template>
  <section class="container">
    <div
      class="grid place-items-center lg:max-w-screen-xl gap-8 mx-auto pt-20 md:py-32"
    >
      <div class="text-center space-y-8">

        <div
          class="max-w-screen-md mx-auto text-center text-5xl md:text-6xl font-bold"
        >
          <h1>
            Créer la  
            <span
              class="text-transparent bg-gradient-to-r from-[#eb2424] to-primary bg-clip-text"
              >Vidéo parfaite
            </span>
            <br />
            pour vos campagnes
          </h1>
        </div>

        <p class="max-w-2xl mx-auto text-xl text-muted-foreground">
          Pourquoi se limiter à une simple vidéo de présentation ?
          Créons ensemble une vraie histoire qui met en valeur votre thème et votre engagement.
        </p>

        <div class="space-y-4 md:space-y-0 md:space-x-4">
          <Button class="w-5/6 md:w-1/4 font-bold group/arrow">
            <a
              href="#contact"

              > C'est partit</a
            >
           
            <ArrowRight
              class="size-5 ml-2 group-hover/arrow:translate-x-1 transition-transform"
            />
          </Button>

          <Button
            as-child
            variant="secondary"
            class="w-5/6 md:w-1/4 font-bold"
          >
            <a
              href="#videos"

              >Voir mes créations</a
            >
          </Button>
        </div>
      </div>

    </div>
  </section>
</template>

<style scoped>
.img-shadow-animation {
  animation-name: img-shadow-animation;
  animation-iteration-count: infinite;
  animation-duration: 2s;
  animation-timing-function: linear;
  animation-direction: alternate;
}

.img-border-animation {
  animation-name: img-border-animation;
  animation-iteration-count: infinite;
  animation-duration: 2s;
  animation-timing-function: linear;
  animation-direction: alternate;
}

@keyframes img-shadow-animation {
  from {
    opacity: 0.5;
    transform: translateY(30px);
  }

  to {
    opacity: 1;
    transform: translateY(0px);
  }
}
@keyframes img-border-animation {
  from {
    @apply border-t-primary/10;
  }

  to {
    @apply border-t-primary/60;
  }
}
</style>
