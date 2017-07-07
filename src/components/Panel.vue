<template>
    <div class="panel">
        <button class="panel__header panel--active">
            {{ title }}
            <indicator />
        </button>
        <ul class="panel__body">
            <li class="panel__item" v-for="item in items">
                <span v-html="item.subject"></span> - <strong class="text--danger">{{ item.grade }}</strong>
            </li>
        </ul>
    </div>
</template>

<script>
import indicator from '../assets/images/indicator.svg'

export default {
    name: 'panel',
    props: {
        title: String,
        items: Array
    },
    data () {
        return {}
    },
    components: {
        indicator
    }
}
</script>

<style scoped>

</style>
