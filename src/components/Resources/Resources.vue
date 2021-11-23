<template>
  <div class="resources">
    <div class="tabs">
      <button @click="setSelectedTab('StoreResources')" :class="isFlatStore">
        Store Resources
      </button>
      <button @click="setSelectedTab('AddResource')" :class="isFlatAdd">
        Add Resources
      </button>
    </div>
    <component :is="selectedTab" :resources="resources"></component>
  </div>
</template>
<script>
import AddResource from "./AddResource.vue";
import StoreResources from "./StoreResources.vue";
export default {
  name: "Resources",
  components: {
    AddResource,
    StoreResources,
  },
  data() {
    return {
      selectedTab: "StoreResources",
      resources: [],
    };
  },
  provide() {
    return {
      addResource: this.addResource,
      deleteResource: this.deleteResource,
    };
  },
  methods: {
    getLocalStorage(name) {
      return JSON.parse(localStorage.getItem(name));
    },
    setLocalStorage(name, data) {
      localStorage.setItem(name, JSON.stringify(data));
    },
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addResource(title, description, url) {
      const newResource = { title: title, description: description, link: url };
      this.resources.unshift(newResource);
      this.setLocalStorage("resources", this.resources);
      this.getLocalStorage("resources");
      this.selectedTab = "StoreResources";
    },
    deleteResource(index) {
        this.resources = JSON.parse(localStorage.resources);
        this.resources.splice(index, 1);
    }
  },
  computed: {
    isFlatStore() {
      return this.selectedTab == "StoreResources" ? null : "flat";
    },
    isFlatAdd() {
      return this.selectedTab == "AddResource" ? null : "flat";
    },
  },
  watch: {
    resources: {
      handler(newResource) {
        localStorage.resources = JSON.stringify(newResource);
      },
      deep: true,
    },
  },
  mounted() {
    const resources = this.getLocalStorage("resources");
    if (resources.length) {
      this.resources = resources;
    } else {
      this.setLocalStorage("resources", []);
    }
  },
};
</script>
<style scoped>
.resources {
  max-width: 40rem;
  margin: 0 auto;
}
.tabs {
  border-radius: 12px;
  box-shadow: 0 2px 8px rgb(0 0 0 / 26%);
  padding: 1rem;
  margin: 2rem auto;
  max-width: 40rem;
}
</style>