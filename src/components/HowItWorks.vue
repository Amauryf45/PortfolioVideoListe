<script setup lang="ts">
import { Card, CardContent, CardHeader, CardTitle } from "@/components/ui/card";
import { Badge } from "@/components/ui/badge";

import { useColorMode } from "@vueuse/core";
const mode = useColorMode();

interface HowItWorksProps {
  badgeTitle: string;
  title: string;
  description: string;
  imageLight: string;
  imageDark: string;
}

const HowItWorksList: HowItWorksProps[] = [
  {
    badgeTitle: "Étape 1",
    title: "La pré-production",
    description:
      "Rediger le script, concevoir le storyboard et rechercher les lieux de tournage.",
    imageLight: "director - light.png",
    imageDark: "director - dark.png",
  },
  {
    badgeTitle: "Étape 2",
    title: "La réalisation",
    description:
      "Tournage et mise en scène selon le plan établi avec tous les membres de votre liste.",
    imageLight: "clap - light.png",
    imageDark: "clap - dark.png",
  },
  {
    badgeTitle: "Étape 3",
    title: "La post-production",
    description:
      "Montage, visuel et mixage pour sublimer chaque détail.",
    imageLight: "edit - light.png",
    imageDark: "edit - dark.png",
  },
];
</script>

<template>
  <section
    id="features"
    class="container py-24 sm:py-32"
  >
    <div class="text-center mb-8">
      <h2 class="text-lg text-primary text-center mb-2 tracking-wider">
        Comment ça marche ?
      </h2>

      <h2 class="text-3xl md:text-4xl text-center font-bold">
        Processus étape par étape
      </h2>
    </div>

    <div class="lg:w-[80%] mx-auto relative">
      <div
        v-for="(
          { badgeTitle, title, description, imageLight, imageDark }, index
        ) in HowItWorksList"
        :key="title"
        :class="[
          'flex flex-col lg:flex-row mb-20 items-center',
          { 'lg:flex-row-reverse flex-col-reverse': index % 2 !== 0 },
        ]"
      >
        <Card class="h-full bg-transparent border-0 shadow-none">
          <CardHeader>
            <div class="pb-4">
              <Badge>{{ badgeTitle }}</Badge>
            </div>

            <CardTitle>
              {{ title }}
            </CardTitle>
          </CardHeader>

          <CardContent class="text-muted-foreground w-[80%]">
            {{ description }}
          </CardContent>
        </Card>

        <img
          :src="mode === 'light' ? `${imageLight}` : `${imageDark}`"
          :alt="`Image describing ${title} `"
          :class="['w-[150px]  md:w-[250px] lg:w-[300px] mx-auto -scale-x-100 absolute right-0',
          {
              'lg:left-0 lg:right-auto': index % 2 !== 0,
            },
            ]"
        />
        <div
          :class="[
            '-z-10 absolute right-0 w-44 h-72  lg:w-64 lg:h-80 rounded-full bg-primary/15 dark:bg-primary/10 blur-3xl',
            {
              'lg:left-0 lg:right-auto': index % 2 !== 0,
            },
          ]"
        ></div>
      </div>
    </div>
  </section>
</template>
