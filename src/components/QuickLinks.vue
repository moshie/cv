<template>
    <ul class="quick-links">
        <li class="quick-links__item">
            <Twitter />
            <a :href="twitterLink" class="quick-links__link" title="David Hewitt's twitter profile" target="_blank">
                @{{ twitter }}
            </a>
        </li>
        <li class="quick-links__item">
            <Print />
            <button type="button" href="#" class="quick-links__link">
                Print page
            </button>
        </li>
        <li class="quick-links__item">
            <Github />
            <a :href="githubLink" class="quick-links__link" title="David Hewitt's github profile" target="_blank">
                {{ github }}
            </a>
        </li>
        <li class="quick-links__item">
            <Star />
            <button type="button" href="#" class="quick-links__link">
                Bookmark
            </button>
        </li>
    </ul>
</template>

<script>
import Print from '../assets/images/print.svg'
import Star from '../assets/images/star.svg'
import Twitter from '../assets/images/twitter.svg'
import Github from '../assets/images/github.svg'

export default {
    name: 'quick-links',
    props: {
        twitter: String,
        github: String
    },
    computed: {
        twitterLink: function () {
            return `https://twitter.com/${this.twitter}`
        },
        githubLink: function () {
            return `https://github.com/${this.github}`
        }
    },
    data () {
        return {}
    },
    components: {
        Twitter,
        Github,
        Star,
        Print
    }
}
</script>

<style scoped>

</style>
