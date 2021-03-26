<template>
  <AppLoader v-if="isLoading" />
  <div class="app">
    <Group  v-for="group in groups" :key="group.id" :group="group"></Group>
  </div>
  <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Group from './components/Group.vue'
import AppLoader from './components/AppLoader.vue'
// import vClickOutside from 'v-click-outside'
//
export default {
    name: 'App',
    components: {
        // HelloWorld,
        Group,
        AppLoader,
    },
    directives: {
        //  clickOutside: vClickOutside.directive
    },
    methods: {
         test() {
            console.log('test');
        },
        getData() {
            const groups = [
                {
                    group_id: 0,
                    name: 'Complain, whimper, cry, annoy',
                    order: 1,
                    rows: [
                        {
                            row_id: 0,
                            shade: 'Complain',
                            word_list: [
                                {
                                    word_id: 0,
                                    lexeme: 'Complain',
                                    intransitive: true,
                                    meaning: [
                                        'when you complain you say that you are not satisfied with it;',
                                        'of (of pain or illness), that you are feeling pain or ill',
                                    ],
                                    shade: 'to say your dissatisfaction',
                                    examples: null,
                                },
                                {
                                    word_id: 1,
                                    lexeme: 'Remonstrate (with sb) (about sth)',
                                    intransitive: true,
                                    transitive: true,
                                    formal: true,
                                    meaning:[ 'you protest them about something you do not approve of or agree with and you try to get it changed or stopped'],
                                    shade: 'YOU DO NOT APPROVE AND WANT IT STOPPED OR CHANGED',
                                    examples: [
                                        'I went to the boss to remonstrate against the new rules;',
                                        'The editor remonstrated with him about the inaccuracies in the story;',
                                        'He remonstrated with the referee',
                                    ]
                                },
                                {
                                    word_id: 2,
                                    lexeme: 'expostulate',
                                    intransitive: true,
                                    formal: true,
                                    meaning: ['to express strong disagreement with someone'],
                                    shade: 'STRONG DISAGREEMENT',
                                    examples: null,
                                }
                            ],
                            rows: [
                                {
                                    row_id: 1,
                                    shade: 'irritating with whine',
                                    word_list: [
                                        {
                                            word_id: 3,
                                            lexeme: 'bleat',
                                            intransitive: true,
                                            informal: true,
                                            dissaproving: true,
                                            meaning: [
                                                'complain about in a way which makes them sound weak and irritating',
                                            ],
                                            shade: 'WHICH SOUNDS WEAK AND IRRITATING',
                                            examples: [
                                                'She’s always bleating (on) about how badly she’s been treated'
                                            ],
                                        },
                                    ]
                                }
                            ]
                        }
                    ]
                }
                    ];
            return new Promise((resolve) => {
                // setTimeout(() => {
                    return resolve(groups);
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
body {
    font-family: 'Source Sans Pro', sans-serif;
}

.app {
    display: grid;
    gap: 10px;
	/* grid-template-columns: 3fr 1fr; */
}

.content {

}
</style>
