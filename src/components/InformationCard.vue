<template>
  <div class="information-block">
    <div class="wrapper-cross">
      <slot name="cross"></slot>
    </div>
    <div>
      <div class="icon-block">
        <img
          src="@/assets/images/info-blue.svg"
          alt=""
          class="icon-block-img"
        />
        <h3 v-html="$t('pages.contribute.tutorial_title')" class="title" />
      </div>
      <p
        class="information-text"
        v-html="$t('pages.contribute.tutorial_desc')"
      />
    </div>
    <slot name="button"></slot>
  </div>
</template>

<script setup lang="ts"></script>

<style scoped>
h3 {
  padding: 0;
  margin: 0;
}
.title {
  font-size: 1.6rem;
  color: var(--blue-dark);
  margin-bottom: 0;
}
.information-block {
  position: relative;
  border-left: 1.4rem solid var(--blue);
  padding: 1.8rem 1.8rem 1.3rem;
  background-color: var(--blue-pale);
  border-radius: 1.5rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  width: fit-content;
  margin-top: 3rem;
}
.wrapper-cross {
  position: absolute;
  top: 1rem;
  right: 1rem;
}
.icon-block {
  display: flex;
  align-items: center;
  margin-bottom: 0.5rem;
}
.icon-block-img {
  margin-right: 0.5rem;
  height: 2.2rem;
}
.information-text {
  margin-top: 1rem;
  font-size: 1.6rem;
  white-space: pre-wrap;
}
@media (max-width: 768px) {
  .title,
  .information-text {
    font-size: 1.4rem;
  }
  .information-block {
    border-left: 1rem solid var(--blue);
  }
  .icon-block {
    flex-direction: column;
    align-items: flex-start;
  }
}
</style>
