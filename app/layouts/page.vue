<script setup lang="ts">
const { t } = useI18n()

const { toggleLocale } = useLocale()

const { headerLogo } = storeToRefs(useLayoutStore())

function openGithub() {
  window.open(GITHUB_URL)
}
</script>

<template>
  <main px-4>
    <header py-8 text-center>
      <img v-if="headerLogo" mx-auto alt="Logo Image" src="/logo.png" w-20>
      <h1>
        <span mr-2 font-800>{{ t('app.title') }}</span>
        <sup><i>v{{ APP_VERSION }}</i></sup>
      </h1>
      <div flex="~ wrap gap-2 justify-center">
        <TheButton @click="toggleLocale()">
          <i i-carbon-ibm-watson-language-translator />
        </TheButton>
        <TheButton @click="toggleDark()">
          <i i="carbon-sun dark:carbon-moon" />
        </TheButton>
        <TheButton @click="openGithub()">
          <i i="carbon-logo-github" />
        </TheButton>
      </div>
    </header>
    <main m-auto min-h-32 max-w-full sm:max-w-2xl>
      <slot />
    </main>
    <footer flex="~ items-center justify-center gap-2" py-8>
      <a :href="LICENSE_URL" target="_blank">MIT License</a>
      <span> © {{ new Date().getFullYear() }} </span>
      <a :href="AUTHOR_URL" target="_blank">Kieran Wang</a>
    </footer>
  </main>
</template>
