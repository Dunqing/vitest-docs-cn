<script setup lang="ts">
import type { CoreTeam } from '../contributors'
defineProps<{
  avatar: CoreTeam['avatar']
  name: CoreTeam['name']
  github: CoreTeam['github']
  twitter: CoreTeam['twitter']
  sponsors: CoreTeam['sponsors']
  description: CoreTeam['description']
}>()
</script>

<template>
  <div text-left flex="~ row gap6" relative>
    <img
      loading="lazy"
      width="100" height="100"
      rounded-full min-w-25 min-h-25 h-25 w-25
      inline-block
      :src="avatar"
      :alt="`${name}'s avatar`"
    >
    <div flex="~ col gap2">
      <div text-2xl>
        {{ name }}
      </div>
      <div op60 v-html="description" />
      <div flex="~ inline gap-2" text-2xl>
        <a
          class="i-carbon-logo-github inline-block !text-current op30 hover:op100 mya transition duration-200"
          :href="`https://github.com/${github}`"
          target="_blank"
          rel="noopener noreferrer"
          :aria-label="`${name} on GitHub`"
        />
        <a
          v-if="twitter"
          class="i-carbon-logo-twitter inline-block text-1.3em mya !text-current op30 hover:op100 transition duration-200"
          :href="`https://twitter.com/${twitter}`"
          target="_blank"
          rel="noopener noreferrer"
          :aria-label="`${name} on Twitter`"
        />
      </div>
    </div>
    <a
      v-if="sponsors"
      class="btn bg-pink-500 hover:bg-pink-600 text-sm !text-white px3 absolute top-1 right-1"
      flex="~ row gap-2"
      target="_blank"
      rel="noopener noreferrer"
      :href="`https://github.com/sponsors/${github}`"
    >
      <span class="i-carbon-favorite-filled" />
      Sponsor
    </a>
  </div>
</template>
