<template>
    <form class="form">
        <slot name="description"></slot>

        <div class="form__group form--has-error">
            <label for="name" class="sr-only">Full name</label>
            <input type="text" name="name" id="name" placeholder="Name" class="form__field">
        </div>

        <div class="form__group form--has-success">
            <label for="email" class="sr-only">Email</label>
            <input type="email" name="email" id="email" placeholder="Email" class="form__field">
        </div>

        <div class="form__group">
            <label for="message" class="sr-only">Message</label>
            <textarea name="message" id="message" placeholder="Message" class="form__field" cols="4"></textarea>
        </div>

        <div class="form__group">
            <button type="submit" class="button__primary">Send</button>
        </div>
    </form>
</template>

<script>
export default {
    name: 'contact-form',
    props: {},
    data () {
        return {}
    },
    components: {}
}
</script>

<style scoped>

</style>
