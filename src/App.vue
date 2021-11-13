<template>
    <ui-top-app-bar
    content-selector="#content-main"
    :type="type"
    :title="title"
    @nav="openDrawer = true"
  >
    <template #toolbar="{ toolbarItemClass }">
      <ui-icon-button
        :class="toolbarItemClass"
        icon="file_download"
      ></ui-icon-button>
      <ui-icon-button :class="toolbarItemClass" icon="print"></ui-icon-button>
      <ui-icon-button
        :class="toolbarItemClass"
        icon="bookmark"
      ></ui-icon-button>
    </template>
  </ui-top-app-bar>
  asd
</template>
<script lang="ts">

</script>
<style>

</style>