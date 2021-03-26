<template>
<div class="word">
    <div class="word__meta">
        <div class="word__meta-item word__type">{{this.type}}</div>
        <div class="word__meta-item word__transitivity">
            <span class="word__intransitive" v-if="intransitive">I</span>
            <span class="word__transitive" v-if="transitive">T</span>
        </div>
    </div>
    <slot></slot>
</div>
</template>

<script>

export default {
    props: [
        'type',
        'transitive',
        'intransitive',
    ],
    name: 'Word',
    data() {
        return {

        }
    }
}
</script>

<style>
.word {
	display: flex;
	position: relative;
	padding: 25px 10px 10px;
	border: 1px solid #eaeaea;
	margin: 0 5px;
	font-size: 30px;
}
.word__meta {
    display: flex;
    position: absolute;
    top: 10px;
    text-transform: uppercase;
    font-weight: bold;
    margin-bottom: 5px;
    font-size: 14px;
}

.word__meta-item {
    margin-right: 5px;
    font-family: sans-serif;
}

.word__meta-item span {
    font-family: sans-serif;
}
</style>
