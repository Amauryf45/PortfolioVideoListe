<script setup lang="ts">
import { Card, CardContent, CardTitle } from "@/components/ui/card2";
import { GraduationCap, Rocket, Users, Clapperboard } from "lucide-vue-next";

interface StoryItem {
  icon?: string;
  title: string;
  logos?: Array<{ alt: string; src: string }>;
}

const storyList: StoryItem[] = [
  {
    icon: "graduation",
    title: "Ancien élève d'IMT Mines Alès — Promo FIG 173",
    logos: [
      { alt: "IMT Mines Alès", src: "public/imt-mines-ales.svg" }, // << remplace le chemin
    ],
  },
  {
    icon: "rocket",
    title: "BDE Hierog'list & projets d'école (Komi, UberEMA...)",
    logos: [
      { alt: "BDE Hierog'list", src: "public/Hieroglist.png" }, // << remplace
      { alt: "Komi", src: "public/Komi.png" }, // << remplace
    ],
  },
  {
    icon: "users",
    title: "Ancien ambassadeur étudiant (Konect Group, Karos)",
    logos: [
      { alt: "Konect", src: "public/Konect.jpeg" }, // << remplace
      { alt: "Karos", src: "public/Karos.png" }, // << remplace
    ],
  },
  {
    icon: "clapperboard",
    title: "De nombreux projets vidéo liés à la vie associative",
    logos: [
      { alt: "Down", src: "public/arrowDown.png" }, // << remplace
    ], // ajoute des logos si tu en as pour les assos
  },
];

const iconMap: Record<string, any> = {
  graduation: GraduationCap,
  rocket: Rocket,
  users: Users,
  clapperboard: Clapperboard,
};
</script>

<template>
  <section id="who-am-i" class="container mt-4 pb-4 sm:pb-32">
    <div class="relative group overflow-hidden">
      <!-- gradient shadow -->
      <div
        class="absolute -top-6 right-12 w-[90%] h-12 lg:h-[80%] bg-primary/50 blur-3xl rounded-full img-shadow-animation -z-10 pointer-events-none"
      />
      <div><br /></div>
      <!-- gradient effect img -->
      <div
        class="absolute bottom-0 left-0 w-full h-20 md:h-28 bg-gradient-to-b from-background/0 via-background/50 to-background rounded-lg -z-10 pointer-events-none"
      />
    </div>

    <h2 class="text-lg text-primary text-center mt-16 mb-2 tracking-wider">
      Avant tout
    </h2>
    <h2 class="text-3xl md:text-4xl text-center font-bold mb-16">
      Qui je suis ?
    </h2>

    <div class="grid lg:grid-cols-[60%_40%] place-items-center lg:gap-4">
      <!-- Colonne texte -->
      <div class="grid gap-4 w-full">
        <Card
          v-for="({ icon, title, logos }, idx) in storyList"
          :key="idx"
          class="bg-muted/50 dark:bg-card hover:bg-background dark:hover:bg-background grayscale opacity-80 hover:grayscale-0 hover:opacity-100 transition-all delay-75 group/story"
        >
          <CardContent>
            <div class="flex items-start m-4 justify-between gap-3">
              <div class="flex items-center gap-3">
                <component
                  v-if="icon"
                  :is="iconMap[icon]"
                  class="size-8 text-primary shrink-0"
                />
                <CardTitle class="leading-tight">{{ title }}</CardTitle>
              </div>
              <!-- Logos -->
              <div
                v-if="logos && logos.length"
                class="flex flex-wrap items-center gap-4 pr-3"
              >
                <img
                  v-for="logo in logos"
                  :key="logo.alt"
                  :src="logo.src"
                  :alt="logo.alt"
                  class="h-8 md:h-10 object-contain"
                  loading="lazy"
                />
              </div>
            </div>
          </CardContent>
        </Card>
      </div>

      <!-- Colonne photo -->
      <div class="w-full flex justify-center">
        <img
          src="public/Me.JPG"
          alt="Moi"
          class="w-[180px] md:w-[260px] lg:w-[380px] mx-auto rounded-xl shadow-lg"
        />
      </div>
    </div>
  </section>
</template>

<style lang="less" scoped></style>
