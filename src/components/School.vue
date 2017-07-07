<template>
    <div class="school">
        <school />
        <span class="school__title">{{ title }}</span>
        <span class="school__date">
            <time :datetime="startAttribute">{{ start }}</time> - 
            <time :datetime="endAttribute">{{ end }}</time>
        </span>
    </div>
</template>

<script>
import school from '../assets/images/school.svg'

export default {
    name: 'accordion',
    props: {
        title: String,
        start: String,
        end: String
    },
    computed: {
        startAttribute: function () {
            return this.start
        },
        endAttribute: function () {
            return this.end
        }
    },
    components: {
        school
    }
}
</script>

<style scoped>

</style>
