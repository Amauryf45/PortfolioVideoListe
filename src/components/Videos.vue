<script setup lang="ts">
import { Card, CardContent, CardHeader, CardTitle } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import {
  Dialog,
  DialogContent,
  DialogHeader,
  DialogTitle,
  DialogTrigger,
} from "@/components/ui/dialog";

interface VideoItem { 
  id: string;        // YouTube ID
  title: string;
  description?: string;
}

const videos: VideoItem[] = [
  { id: "CBWaWmRSQaw", title: "Vidéo Interstell'Art" },
  { id: "GQK19yeC0hg", title: "Clip RAP" },
  { id: "wrtsi5VQurE", title: "Vidéo Cambriol'Art" },
  { id: "sBWZqOolOQg", title: "Teaser Komi" },
];

// Helper thumb
const ytThumb = (id: string) => `https://img.youtube.com/vi/${id}/hqdefault.jpg`;
</script>

<template>
  <section id="videos" class="container pb-24 sm:pb-32">


    <h2 class="text-3xl md:text-4xl text-center font-bold mb-4">
      Réalisations
    </h2>

    <h3 class="md:w-1/2 mx-auto text-xl text-center text-muted-foreground mb-8">
      Une sélection de vidéos produites pour des assos et projets liées à l'EMA.
    </h3>

      <!-- Colonne carrousel horizontal -->
      <div class="w-full relative">
        <!-- halos/subtle edges -->
        <div class="pointer-events-none absolute inset-y-0 left-0 w-8 bg-gradient-to-r from-background to-transparent rounded-l-lg"></div>
        <div class="pointer-events-none absolute inset-y-0 right-0 w-8 bg-gradient-to-l from-background to-transparent rounded-r-lg"></div>

        <div
          class="flex gap-4 overflow-x-auto snap-x snap-mandatory scroll-smooth pr-2
                 [scrollbar-width:none] [-ms-overflow-style:none] [&::-webkit-scrollbar]:hidden"
        >
          <!-- Chaque carte occupe ~50% en lg => 2 visibles -->
          <Dialog v-for="v in videos" :key="v.id">
            <DialogTrigger as-child>
              <Card
                class="snap-start shrink-0 w-[85%] sm:w-[70%] md:w-[55%] lg:w-[45%]
                       bg-muted/50 dark:bg-card hover:bg-background dark:hover:bg-background
                       grayscale(10%) 
                       hover:grayscale-0 hover:opacity-100 transition-all delay-75 cursor-pointer group"
                title="Cliquer pour lire"
              >
                <CardHeader class="pb-2">
                  <CardTitle class="text-base md:text-lg line-clamp-2">{{ v.title }}</CardTitle>
                </CardHeader>
                <CardContent>
                  <div class="relative aspect-video overflow-hidden rounded-lg">
                    <img
                      :src="ytThumb(v.id)"
                      :alt="v.title"
                      class="w-full h-full object-cover transition duration-300 group-hover:scale-[1.02]"
                      loading="lazy"
                    />
                    <!-- Play overlay -->
                    <div
                      class="absolute inset-0 grid place-items-center bg-black/0 group-hover:bg-black/10 transition"
                    >
                      <div
                        class="h-12 w-12 md:h-14 md:w-14 rounded-full bg-primary/90 grid place-items-center shadow-lg"
                      >
                        <svg viewBox="0 0 24 24" class="h-6 w-6 text-white" aria-hidden="true">
                          <path d="M8 5v14l11-7z" fill="currentColor" />
                        </svg>
                      </div>
                    </div>
                  </div>
                  <p v-if="v.description" class="mt-3 text-sm text-muted-foreground line-clamp-2">
                    {{ v.description }}
                  </p>
                </CardContent>
              </Card>
            </DialogTrigger>

            <!-- Modal lecteur YouTube -->
            <DialogContent class="max-w-3xl">
              <DialogHeader>
                <DialogTitle>{{ v.title }}</DialogTitle>
              </DialogHeader>
              <div class="aspect-video">
                <iframe
                  class="w-full h-full rounded-lg"
                  :src="`https://www.youtube.com/embed/${v.id}?autoplay=1&rel=0`"
                  title="YouTube video player"
                  frameborder="0"
                  allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
                  allowfullscreen
                />
              </div>
            </DialogContent>
          </Dialog>
        </div>
      </div>
      <div class="mt-6 text-center ">
        <a href="/videos">
          <Button size="lg">Voir plus</Button>
        </a>
      </div>
  </section>
</template>
