<script lang="ts" setup>
definePageMeta({
  name: 'dynamic',
  layout: 'page',
})

const { t } = useI18n()

const { back } = useBack()

const route = useRoute()

const title = computed(() => {
  return (route.params.id as string) || ''
})

useHead({
  title,
})
</script>

<template>
  <TheCard>
    <h2 text-center text-lg font-bold mb-5>
      Hi, {{ route.params.id }}
    </h2>
    <p>
      Read more about dynamic routing in the
      <a target="_blank" href="https://uvr.esm.is/guide/file-based-routing.html#dynamic-routes">
        https://uvr.esm.is/guide/file-based-routing.html#dynamic-routes
      </a>
    </p>
    <TheButton mx-auto mt-4 @click="back()">
      <i i-carbon-return mr-2 />
      <span> {{ t('button.back') }}</span>
    </TheButton>
  </TheCard>
</template>
