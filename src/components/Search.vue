<template>
  <form class="form" @submit.stop.prevent="searchVal">
    <div class="form-group d-flex">
      <i class="fa fa-search"></i>
      <input type="search" class="form-control" placeholder="Search city ?" v-model.trim="search"
             @keypress.enter="$event.preventDefault()"/>
      <button type="submit" :class="[search ? 'visible' : '', 'btn btn-secondary']">
        search
      </button>
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      search: "",
    };
  },
  methods: {
    searchVal() {
      this.$emit("search", this.search);
      this.search = ""
    }
  }
};
</script>

<style scoped>
.form-group {
  position: relative;
}

.form-group .form-control {
  padding-left: 2rem;
  padding-right: 5rem;
}

.fa-search {
  position: absolute;
  top: 0;
  bottom: 0;
  transform: translate(8px, 10px);
  pointer-events: none;
  color: var(--bs-gray-500);
}

.btn {
  position: absolute;
  right: 1px;
  transition: 200ms ease-in-out;
  opacity: 0;
  visibility: collapse;
  box-shadow: none !important;
}

.btn.visible {
  opacity: 1;
  visibility: visible;
}
</style>
