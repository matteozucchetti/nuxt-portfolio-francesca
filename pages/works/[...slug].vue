<template>
  <div class="pf-page">
    <div class="pf-content">
      <ContentDoc :path="$route.path">
        <template v-slot="{ doc }">
          <Breadcrumb :text="'WORKS | ' + doc.head" type="p" />
          <div class="pf-contentList">
            <h1>{{ doc.head }}</h1>
            <h2>{{ doc.subhead }}</h2>
            <ContentRenderer :value="doc" />
            <Back style="display: flex"></Back>
          </div>
        </template>
        <template #not-found> <h1>Document not found</h1> </template>
      </ContentDoc>
    </div>
  </div>
</template>

<script setup lang="ts">
definePageMeta({
  pageTransition: {
    name: "page-transiton",
    mode: "out-in",
    onEnter: (el, done) => enterTransition(el, done),
    onLeave: (el, done) => leaveTransition(el, done),
  },
});

const docTitle = ref<string | null>(null);
</script>

<style scoped lang="scss">
@use "/assets/css/mq.scss" as *;
@use "/assets/css/functions.scss" as *;

.pf-contentList {
  height: 100%;
  padding: 50px 100px;

  @include mq($until: lg) {
    padding: 50px 0;
    gap: 50px;
  }

  h1 {
    color: #fff;
    font-family: Montserrat;
    font-size: 46px;
    font-style: normal;
    font-weight: 400;
    line-height: 120%;
    @include mq($until: lg) {
      font-size: 32px;
    }
  }

  h2 {
    color: #616161;
    font-family: Poppins;
    font-size: 16px;
    font-style: normal;
    font-weight: 400;
    line-height: normal;
    letter-spacing: 5.12px;
    text-transform: uppercase;
    margin-bottom: 40px;
    line-height: 1.2;
  }

  :deep(p) {
    color: #fff;
    font-family: Montserrat;
    font-size: 18px;
    font-style: normal;
    font-weight: 300;
    line-height: 120%;
    text-wrap: pretty;
    margin-bottom: 40px;
  }
}
</style>