<script setup>
    import {ref} from 'vue'

    const form = ref({
        name: '',
        email: '',
        message: ''
    })

    // TODO: SEND MESSAGE TO ME
    const submit = () => {
        console.log(form.value)
    }

</script>

<template>
    <div class="contact-container">
        <h1 class="contact-title">Contact Me</h1>
        <form class="contact-form" @submit.prevent="submit">
            <input
                type="text"
                id="name"
                v-model="form.name"
                name="name"
                placeholder="Full Name"
            />
            <input
                type="text"
                id="email"
                v-model="form.email"
                name="email"
                placeholder="Email"
            />
            <input
                type="text"
                id="message"
                v-model="form.message"
                name="message"
                placeholder="Message"
            />
            <button class="contact-button" type="submit">Send Message</button>
        </form>
    </div>
</template>

<style scoped>
    .contact-container {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        background-color: lightgreen;
    }

    form {
        display: flex;
        flex-direction: column;
    }

    form > input {
        padding: 0.2rem;
        margin: 0.2rem;
    }
</style>