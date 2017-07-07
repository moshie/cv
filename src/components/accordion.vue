<template>
    <div class="accordion">
        <button class="accordion__title accordion--active">
            {{ title }}
            <indicator />
        </button>
        <ul class="accordion__panel">
            <li class="accordion__item" v-for="item in items">
                {{ item.title }}
            </li>
        </ul>
    </div>
</template>

<script>
import indicator from '../assets/images/indicator.svg'

export default {
    name: 'accordion',
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
