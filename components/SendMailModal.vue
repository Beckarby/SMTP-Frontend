<script setup lang="ts">
import { Button } from "@/components/ui/button";
import {
  Dialog,
  DialogContent,
  DialogDescription,
  DialogFooter,
  DialogHeader,
  DialogTitle,
  DialogTrigger,
} from "@/components/ui/dialog";
import {
  Form,
  FormControl,
  FormDescription,
  FormField,
  FormItem,
  FormLabel,
  FormMessage,
} from "@/components/ui/form";

import { Input } from "@/components/ui/input";
import { Textarea } from "@/components/ui/textarea";
import { toast } from "@/components/ui/toast";
import { toTypedSchema } from "@vee-validate/zod";
import { h, ref } from "vue";
import * as z from "zod";

const formSchema = toTypedSchema(z.object({
  email: z.string().email({ message: "Please enter a valid email address." }),
  subject: z.string().min(1, { message: "Subject is required." }).max(100),
  content: z.string().optional(),
}));



async function onSubmit(values: any) {
    toast({
      title: "Email sent with the following details:",
      description: h(
        "pre",
        { class: "mt-2 w-[340px] rounded-md bg-slate-950 p-4" },
        h("code", { class: "text-white" }, JSON.stringify(values, null, 2))
      ),
    });
    console.log("Email sent with the following details:", values);
}

const fileInput = ref<HTMLInputElement | null>(null);

function triggerFileInput() {
  console.log("Triggering file input");

  fileInput.value
    ? console.log("File input:", fileInput.value)
    : console.log("File input is null");

  fileInput.value?.click();
}

function handleFileChange(event: Event) {
  const files = (event.target as HTMLInputElement).files;
  if (files && files.length > 0) {
    const file = files[0];
    console.log("Selected file:", file);
  }
}
</script>

<template>
  <Form
    v-slot="{ handleSubmit, errors }"
    as=""
    keep-values
    :validation-schema="formSchema"
  >
    <Dialog>
      <DialogTrigger as-child>
        <Button variant="outline"> Send Email </Button>
      </DialogTrigger>
      <DialogContent class="sm:max-w-[425px]">
        <DialogHeader>
          <DialogTitle>Send Email</DialogTitle>
          <DialogDescription>
            Fill in the details below to send an email. Click send when you're
            done.
          </DialogDescription>
        </DialogHeader>

        <form id="dialogForm" @submit="handleSubmit($event, onSubmit)">
          <FormField v-slot="{ componentField }" name="email">
            <FormItem>
              <FormLabel class="form-item-title">Email</FormLabel>
              <FormControl>
                <Input
                  type="email"
                  placeholder="example@example.com"
                  v-bind="componentField"
                />
              </FormControl>
<!--               <FormMessage v-if="errors.email">{{ errors.email }}</FormMessage> -->
              <FormMessage />

            </FormItem>
          </FormField>

          <FormField v-slot="{ componentField }" name="subject">
            <FormItem>
              <FormLabel class="form-item-title">Subject</FormLabel>
              <FormControl>
                <Input
                  type="text"
                  placeholder="Subject"
                  v-bind="componentField"
                />
              </FormControl>
<!--               <FormMessage v-if="errors.subject">{{
                errors.subject
              }}</FormMessage> -->
              <FormMessage />

            </FormItem>
          </FormField>

          <FormField v-slot="{ componentField }" name="content">
            <FormItem>
              <FormLabel class="form-item-title">Content</FormLabel>
              <FormControl>
                <Textarea
                  class="resize-none"
                  placeholder="Write your message here..."
                  v-bind="componentField"
                />
              </FormControl>
<!--               <FormMessage v-if="errors.content">{{
                errors.content
              }}</FormMessage> -->
              <FormMessage />

            </FormItem>
          </FormField>
        </form>
        
                <DialogFooter>
                  <Button variant="outline" @click="triggerFileInput"> Attach </Button>
                  <input
                    id="fileInput"
                    type="file"
                    class="hidden"
                    @change="handleFileChange"
                    ref="fileInput"
                  />
                </DialogFooter>
        <Button type="submit" form="dialogForm"> Send </Button>
      </DialogContent>
    </Dialog>
  </Form>
</template>

<style scoped>
.form-item-title {
  color: rgb(255, 255, 255);
}

.hidden {
  display: none;
}
</style>
