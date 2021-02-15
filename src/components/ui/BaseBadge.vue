<template>
  <span class="badge" :class="['badge--' + mode, { nml: noMarginLeft }]">
    <slot></slot>
  </span>
</template>

<script>
export default {
  props: ['mode', 'noMarginLeft']
};
</script>

<style scoped>
.badge {
  display: inline-block;
  padding: 1.25rem 1rem;
  background-color: #ccc;
  color: #292929;
  /* margin: 0 0.75rem; */
  border-radius: 50%;
}

.nml {
  margin-left: 0;
}

.badge--highlight {
  background-color: var(--clr-accent-500);
  color: black;
}

.badge--elegant {
  background-color: #45006d;
  color: white;
}
</style>
