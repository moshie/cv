<template>
<ul class="timeline">
    <li class="timeline__item" v-for="item in items">
        <span class="timeline__title">{{ item.company }}</span>
        <span class="timeline__time">
            <time datetime="">{{ item.start }}</time> - 
            <span v-html="item.end"></span>
        </span>
    </li>
</ul>
</template>

<script>
export default {
    name: 'timeline',
    props: {
        items: Array
    },
    data () {
        return {}
    },
    components: {}
}
</script>

<style scoped>

</style>
