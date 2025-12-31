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
    <div class="contact-section">
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
                <textarea
                    type="text"
                    id="message"
                    class="message-input"
                    v-model="form.message"
                    name="message"
                    placeholder="Message"
                />
                <button class="contact-button" type="submit">Send Message</button>
            </form>
            
            <hr class="line-break"/>
            
            <div class="contact-links">
                <a href="https://www.linkedin.com/in/robeusanio/"><img src="" alt="LinkedIn Icon"/></a>
                <a href="https://github.com/robeusanio11"><img src="" alt="Github Icon"/></a>
            </div>
        </div>
    </div>
</template>

<style scoped>
    .contact-section {
        background-color: lightgreen;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    .contact-container {
        border-style: solid;
        padding: 1rem;
        /* padding-left: 10rem;
        padding-right: 10rem; */
        min-width: 45%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    form {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        width: 100%;
    }

    form > input, form > textarea {
        width: 50%;
        padding: 1rem;
        margin: 0.75rem;
        border-radius: 20px;
    }

    .message-input {
        width: 70%;
        height: 10em;
    }

    form > button {
        width: 50%;
        padding: 1rem;
        margin: 1rem;
        margin-bottom: 0.5rem;
        border-radius: 20px;
    }

    hr {
        display: block;
        height: 1px;
        width: 95%;
        border: 0;
        border-top: 1px solid black;
        margin: 1em;
        padding: 0;
    }

    .contact-links {
        margin: 0.5rem;
    }

    .contact-links > a {
        margin: 1rem;
    }

</style>