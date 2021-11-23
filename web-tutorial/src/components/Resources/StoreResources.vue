<template>
    <div class="main" v-if="!resources || !resources.length">
        <span><b>No resources have been added yet.</b></span>
    </div>
    <ul class="main">
      <li v-for="(resource, index) in resources" :key="index">
        <div>
          <header class="title">
            <h2>{{resource.title}}</h2>
            <button @click="deleteResource(index)">Delete</button>
          </header>
          <p class="description">{{resource.description}}</p>
          <nav class="link">
            <a :href="resource.link" target="_blank">View Resource</a>
          </nav>
        </div>
      </li>
    </ul>
</template>
<script>
export default {
    name: 'StoreResources',
    inject: ['deleteResource'],
    props: {
        resources: {
            type: Array,
            default: () => []
        }
    }
};
</script>
<style scoped>
span {
    padding-left: 10px;
}
.main {
    max-width: 100%;
    height: 130px;
    background-color: #FFF;
    margin: 0 auto;
    font-family: 'Roboto', sans-serif;
    padding-inline-start: 0;
}
.main li {
    padding: 0;
    margin: auto;
    max-width: 100%;
    list-style: none;
}
.main div {
    border-radius: 10px;
    box-shadow: 0 2px 8px rgba(0, 0 ,0 , 0.3);
    padding: 1rem;
    margin: 2rem auto;
    max-width: 100%;
}
.main header {
    display: flex;
    align-items: center;
    justify-content: space-between;
}
.title {
    font-size: 1.2rem;
    font-weight: bold;
    color: #000;
    font-family: inherit;
}
.title button {
    font-size: 1rem;
    padding: 0.75rem;
    font-family: inherit;
    color: #3a0061;
    margin: 0 15px;
    border: none;
    outline: none;
    cursor: pointer;
    border: 1px solid transparent;
    transition: all 0.5s;
    border-radius: 10px;
    background-color: #FFF;
}
.title button:hover {
    background-color: rgba(39, 0, 65, 0.5);
    border-color: #FFF;
}
.title button:active {
    background-color: rgba(39, 0, 65, 1);
    border-color: #FFF;
    color: #FFF;
}
.description {
    margin: 0.5rem 0;   
    font-family: inherit;
    font-size: 1rem;
    font-style: normal;
}
.link {
    margin: 0.5rem 0;   
}
.link a{
    text-decoration: none;
    color: #ce5c00;
}
</style>