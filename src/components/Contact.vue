<script setup lang="ts">
import { ref, reactive } from "vue";
import { Button } from "./ui/button";
import { Card, CardHeader, CardContent, CardFooter } from "./ui/card";
import { Label } from "./ui/label";
import { Input } from "./ui/input";
import {
  Select,
  SelectContent,
  SelectGroup,
  SelectItem,
  SelectTrigger,
  SelectValue,
} from "./ui/select";
import { Textarea } from "./ui/textarea";
import { Alert, AlertDescription, AlertTitle } from "@/components/ui/alert";

import { AlertCircle, Phone, Mail } from "lucide-vue-next";

interface ContactFormeProps {
  firstName: string;
  lastName: string;
  email: string;
  subject: string;
  message: string;
}

const contactForm = reactive<ContactFormeProps>({
  firstName: "",
  lastName: "",
  email: "",
  subject: "BDE",
  message: "",
});

const invalidInputForm = ref<boolean>(false);

const handleSubmit = () => {
  const { firstName, lastName, email, subject, message } = contactForm;
  console.log(contactForm);

  const mailToLink = `mailto:amaury.fumard@gmail.com?subject=${subject}&body=Salut ! Je suis ${firstName} ${lastName}, mon email est ${email}. %0D%0A${message}`;

  window.location.href = mailToLink;
};
</script>

<template>
  <section
    id="contact"
    class="container py-24 sm:py-32"
  >
    <section class="grid grid-cols-1 md:grid-cols-2 gap-8">
      <div>
        <div class="mb-4">
          <h2 class="text-lg text-primary mb-2 tracking-wider">Informations</h2>

          <h2 class="text-3xl md:text-4xl font-bold">Prendre contact avec moi</h2>
        </div>
        <p class="mb-8 text-muted-foreground lg:w-5/6">
          N'hésitez pas à prendre contact avec moi pour discuter des vos projets de vidéo. <br>
          Ne me parlez pas du thème de votre liste tout de suite s'il vous plaît 🙏 <br>
          Parlons d'abord de vos besoins, de vos moyens et de vos disponibilités !
        </p>

        <div class="flex flex-col gap-4">

          <div>
            <div class="flex gap-2 mb-1">
              <Phone />
              <div class="font-bold">Appel / SMS / WhatsApp</div>
            </div>

            <div>+33 6 51 63 42 84</div>
          </div>

          <div>
            <div class="flex gap-2 mb-1">
              <Mail />
              <div class="font-bold">E-mail</div>
            </div>

            <div>amaury.fumard@gmail.com</div>
          </div>
        </div>
      </div>

      <!-- form -->
      <Card class="bg-muted/60 dark:bg-card">
        <CardHeader class="text-primary text-2xl"> </CardHeader>
        <CardContent>
          <form
            @submit.prevent="handleSubmit"
            class="grid gap-4"
          >
            <div class="flex flex-col md:flex-row gap-8">
              <div class="flex flex-col w-full gap-1.5">
                <Label for="first-name">Prénom</Label>
                <Input
                  id="first-name"
                  type="text"
                  placeholder="Tom"
                  v-model="contactForm.firstName"
                />
              </div>

              <div class="flex flex-col w-full gap-1.5">
                <Label for="last-name">Nom</Label>
                <Input
                  id="last-name"
                  type="text"
                  placeholder="Dubois"
                  v-model="contactForm.lastName"
                />
              </div>
            </div>

            <div class="flex flex-col gap-1.5">
              <Label for="email">Email</Label>
              <Input
                id="email"
                type="email"
                placeholder="mail@gmail.com"
                v-model="contactForm.email"
              />
            </div>

            <div class="flex flex-col gap-1.5">
              <Label for="subject">Sujet</Label>

              <Select v-model="contactForm.subject">
                <SelectTrigger>
                  <SelectValue placeholder="Liste ?" />
                </SelectTrigger>
                <SelectContent>
                  <SelectGroup>
                    <SelectItem value="BDE">
                      BDE
                    </SelectItem>
                    <SelectItem value="BDS">
                     BDS
                    </SelectItem>
                    <SelectItem value="BDA">BDA</SelectItem>
                    <SelectItem value="Autre">Autre</SelectItem>
                  </SelectGroup>
                </SelectContent>
              </Select>
            </div>

            <div class="flex flex-col gap-1.5">
              <Label for="message">Message</Label>
              <Textarea
                id="message"
                placeholder="Message..."
                rows="5"
                v-model="contactForm.message"
              />
            </div>

            <Alert
              v-if="invalidInputForm"
              variant="destructive"
            >
              <AlertCircle class="w-4 h-4" />
              <AlertTitle>Error</AlertTitle>
              <AlertDescription>
                Erreur dans le formulaire.
              </AlertDescription>
            </Alert>

            <Button class="mt-4">Envoyer le message</Button>
          </form>
        </CardContent>

        <CardFooter></CardFooter>
      </Card>
    </section>
  </section>
</template>
