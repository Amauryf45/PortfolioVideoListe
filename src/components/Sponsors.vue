<script setup lang="ts">
import { Marquee } from "@selemondev/vue3-marquee";
import "@selemondev/vue3-marquee/dist/style.css";


interface sponsorsProps {
  icon: { alt: string; src: string };
  name: string;
}

const sponsors: sponsorsProps[] = [
  {
    icon: { alt: "Logo Magiciens", src: "/Magicien.png" },
    name: "Les Magiciens",
  },
  {
    icon: { alt: "Logo Cambriol'Art", src: "/Cambriolart.png" },
    name: "Cambriol'Art",
  },
  {
    icon: { alt: "Logo Interstell'Art", src: "/Interstellart.png" },
    name: "Interstell'Art",
  },
  {
    icon: { alt: "Logo Komi", src: "/Komi.png" },
    name: "Komi",
  },
];
  
const resolveAsset = (path: string) =>
  new URL(path.startsWith("/") ? path : `/${path}`, import.meta.env.BASE_URL).href;

</script>

<template>
  <section
    id="sponsors"
    class="max-w-[75%] mx-auto pb-24 sm:pb-32"
  >
    <h2 class="text-lg md:text-3xl text-center font-bold mb-6">Mes clients vidéos</h2>

    <div class="mx-auto">
      <Marquee
        class="gap-[3rem]"
        :pauseOnHover="true"
        :fade="true"
        innerClassName="gap-[3rem]"
      >
        <div
          v-for="{ icon, name } in sponsors"
          :key="name"
        >
          <div class="flex items-center text-xl md:text-2xl font-medium px-5 gap-3">
            <img
                  :key="icon.alt"
                  :src="resolveAsset(logo.src)"
                  :alt="icon.alt"
                  class="h-8 md:h-10 object-contain"
                  loading="lazy"
                />
            <div class="whitespace-nowrap">{{ name }}</div>
          </div>
        </div>
      </Marquee>
    </div>
  </section>
</template>
