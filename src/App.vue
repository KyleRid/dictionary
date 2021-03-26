<template>
  <AppLoader v-if="isLoading" />
  <div class="app">
    <Group v-for="group in groups" :key="group.id"></Group>
  </div>
  <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Group from './components/Group.vue'
import AppLoader from './components/AppLoader.vue'

export default {
    name: 'App',
    components: {
        // HelloWorld,
        Group,
        AppLoader,
    },
    methods: {
        getData() {
            return new Promise((resolve) => {
                // setTimeout(() => {
                    return resolve([
                        {
                            group_id: 0,
                            order: 1,
                            name: 'Complains',
                            description: null,
                            row_list: [],
                            group_list: []
                        },
                        {
                            group_id: 0,
                            order: 2,
                            name: 'Complains',
                            description: null,
                            row_list: [],
                            group_list: []
                        }
                    ]);
                // }, 5000);
            });

        }
    },
    data() {
        return {
            isLoading: true,
            groups: null,
        }
    },
    async mounted() {
        this.groups = await this.getData();
        this.isLoading = false;
    }
}
</script>

<style>


.app {
    display: grid;
    gap: 10px;
	/* grid-template-columns: 3fr 1fr; */
}

.content {

}
</style>
