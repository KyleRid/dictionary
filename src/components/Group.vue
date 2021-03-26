<template>
  <div class="group" :class="{'collapsed': isCollapsed}">
      <div class="group-heading">
        <button class="group-heading__toggle" @click="toggleGroup">
            V
            <span class="group-heading__title">Complain</span>
        </button>
    </div>
    <Row></Row>
    <!-- <Word></Word> -->
  </div>
</template>

<script>
// import Word from './Word.vue'
import Row from './Row.vue'

export default {
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
    width: 40px;
    height: 40px;
    display: inline-flex;
    align-items: center;
    justify-content: center;
}
</style>
