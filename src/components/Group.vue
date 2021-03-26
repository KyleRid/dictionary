<template>
  <div class="group" :class="{'collapsed': isCollapsed}">
      <div class="group-heading">
        <button class="group-heading__toggle" @click="toggleGroup">
            {{group.order}}
            <i class="fas fa-sort-down"></i>
            <span class="group-heading__title">Complain</span>
        </button>
    </div>
    <Row v-for="row in group.rows" :row="row" :key="row.id"></Row>
    <!-- <Word></Word> -->
  </div>
</template>

<script>
// import Word from './Word.vue'
import Row from './Row.vue'

export default {
    props: ['group'],
    name: 'Group',
    components: {
        // Word,
        Row
    },
    data() {
        return {
            isCollapsed: true,
        }
    },
    methods: {
        toggleGroup() {
            this.isCollapsed = !this.isCollapsed;
        }
    }
}
</script>

<style>
.group {
    padding: 10px;
    border: 1px solid #eaeaea;
    border-radius: 5px;
    text-transform: lowercase;
     /* background-color: rgb(65, 234, 136, 0.55); */
      background-color: #a6ffcb8c;
}

.group .group {
    padding-left: 10px;
}

.group.collapsed > .row {
    height: 0;
    overflow: hidden;
    padding: 0;
}

.group-heading__toggle {
    border-radius: 5px;
    border: 1px solid #eaeaea;
    background: unset;
    /* width: 40px; */
    height: 40px;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    font-size: 25px;
    text-transform: uppercase;
}

.group-heading__toggle:hover {
    cursor: pointer;
    user-select: none;
}

.group-heading__toggle .fas {
    position: relative;
    top: -5px;
    margin-right: 10px;
}

.group-heading__title {
    margin-left: 5px;
    font-family: 'Source Sans Pro', sans-serif;
}
</style>
