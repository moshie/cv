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
            <button type="button" @click="print()" class="quick-links__link">
                Print page
            </button>
        </li>
        <li class="quick-links__item">
            <Github />
            <a :href="githubLink" class="quick-links__link" title="David Hewitt's github profile" target="_blank">
                {{ github }}
            </a>
        </li>
        <!-- <li class="quick-links__item">
            <Star />
            <button type="button" class="quick-links__link">
                Bookmark
            </button>
        </li> -->
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
    methods: {
        print: function () {
            window.print()
        }
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
.quick-links {
    display: flex;
    flex-wrap: wrap;
    margin-bottom: 10px;

    &__item {
        position: relative;
        flex: 0 0 50%;
        margin-bottom: 20px;
        padding-left: 30px;
        padding-top: 3px;
        color: #000;
        min-height: 20px;

        img,
        svg {
            position: absolute;
            top: 0;
            left: 0px;
        }
    }

    &__link {
        text-decoration: none;
        color: #4d4d4d;
        vertical-align: middle;
        background-color: transparent;
        border: 0;
        padding: 0;
        display: inline-block;
        font-size: 14px;
    }

}
</style>
