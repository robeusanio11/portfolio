<script setup>
    import {ref} from 'vue'

    const form = ref({
        name: '',
        email: '',
        message: ''
    })

    // // TODO: SEND MESSAGE TO ME
    const handleSubmit = async (event) => {
        // const curForm = event.target;
        // const formData = new FormData(curForm);

        // await fetch("/", {
        //     method: "POST",
        //     headers: { "Content-Type": "application/x-www-form-urlencoded"},
        //     body: new URLSearchParams(formData).toString()
        // })
        //     .then(() => console.log("Form successfully submitted"))
        //     .catch(error => alert(error))
    }

</script>

<template>
    <div class="contact-section">
        <div class="contact-container">
            <h1 class="contact-title">Contact Me</h1>
            <form class="contact-form" name="contact" @submit.prevent="handleSubmit">
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
                <a href="https://www.linkedin.com/in/robeusanio/"><img src="/lnBug-White.png" title="LinkedIn" alt="LinkedIn Icon"/></a>
                <a href="https://github.com/robeusanio11"><img src="/github-mark-white.png" title="Github" alt="Github Icon"/></a>
            </div>
        </div>
    </div>
</template>

<style scoped>
    .contact-section {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        height: 100%;
        overflow: hidden;
    }

    .contact-container {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        padding: 1.5rem 2rem;
        min-width: 45%;
        max-height: 100%;
        border-radius: 20px;
        border: 2px solid rgba(146, 99, 255, 0.3);
        background-color: rgba(255, 255, 255, .075);
        box-shadow:
            0 0 20px rgba(108, 45, 255, 0.15),
            inset 0 0 30px rgba(108, 45, 255, 0.05);
        transition: all 0.3s ease;
        box-sizing: border-box;
    }

    .contact-container:hover {
        border-color: rgba(146, 99, 255, 0.5);
        box-shadow:
            0 0 30px rgba(108, 45, 255, 0.25),
            inset 0 0 40px rgba(108, 45, 255, 0.08);
    }

    .contact-title {
        color: white;
        font-weight: 400;
        margin: 0 0 1rem 0;
        text-shadow:
            0 0 10px #6c2dffff,
            0 0 20px #6c2dffff,
            0 0 40px rgba(108, 45, 255, 0.5);
    }

    form {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        width: 100%;
        flex: 1;
        min-height: 0;
    }

    form > input, form > textarea {
        width: 50%;
        padding: 0.75rem 1rem;
        margin: 0.5rem;
        border-radius: 20px;
        border: 2px solid rgba(255, 255, 255, 0.2);
        background-color: rgba(0, 0, 0, 0.3);
        color: white;
        font-family: inherit;
        font-size: 1rem;
        transition: all 0.3s ease;
        flex-shrink: 0;
        box-sizing: border-box;
    }

    form > input::placeholder, form > textarea::placeholder {
        color: rgba(255, 255, 255, 0.5);
    }

    form > input:focus, form > textarea:focus {
        outline: none;
        border-color: #9263ffff;
        box-shadow:
            0 0 15px rgba(108, 45, 255, 0.4),
            0 0 30px rgba(108, 45, 255, 0.2);
    }

    .message-input {
        width: 70%;
        flex: 1 1 auto;
        min-height: 5em;
        max-height: 12em;
        resize: none;
    }

    form > button {
        width: 50%;
        padding: 0.75rem 1rem;
        margin: 1rem;
        margin-bottom: 0.25rem;
        border: 2px solid rgba(146, 99, 255, 0.5);
        border-radius: 20px;
        background-color: rgba(108, 45, 255, 0.15);
        color: white;
        font-size: 1rem;
        font-weight: 500;
        cursor: pointer;
        transition: all 0.3s ease;
        flex-shrink: 0;
    }

    form > button:hover {
        border-color: #9263ffff;
        background-color: rgba(108, 45, 255, 0.3);
        box-shadow:
            0 0 20px rgba(108, 45, 255, 0.5),
            0 0 40px rgba(108, 45, 255, 0.3);
        text-shadow: 0 0 10px rgba(255, 255, 255, 0.5);
    }

    form > button:active {
        background-color: rgba(108, 45, 255, 0.4);
        transform: scale(0.97);
    }

    hr {
        display: block;
        height: 1px;
        width: 95%;
        border: 0;
        border-top: 1px solid rgba(146, 99, 255, 0.3);
        margin: 0.75em 0;
        padding: 0;
        flex-shrink: 0;
    }

    .contact-links {
        margin: 0.25rem;
        display: flex;
        gap: 1rem;
        flex-shrink: 0;
    }

    .contact-links > a {
        transition: all 0.3s ease;
    }

    .contact-links > a:hover {
        filter: drop-shadow(0 0 8px #9263ffff) drop-shadow(0 0 15px #6c2dffff);
    }

    img {
        width: 2.5rem;
        height: 2.5rem;
        margin: 0 1rem;
    }

    /* Tablet */
    @media (max-width: 1024px) {
        .contact-container {
            min-width: 60%;
            padding: 1.5rem;
        }

        form > input, form > textarea {
            width: 65%;
        }

        .message-input {
            width: 80%;
        }

        form > button {
            width: 65%;
        }
    }

    /* Mobile */
    @media (max-width: 768px) {
        .contact-container {
            min-width: auto;
            width: 95%;
            padding: 1rem;
        }

        .contact-title {
            font-size: 1.4rem;
            margin: 0 0 0.5rem 0;
        }

        form > input, form > textarea {
            width: 90%;
            padding: 0.65rem 0.85rem;
            margin: 0.35rem;
            font-size: 0.9rem;
        }

        .message-input {
            width: 90%;
            min-height: 4em;
        }

        form > button {
            width: 90%;
            padding: 0.7rem;
            margin: 0.75rem;
        }

        hr {
            margin: 0.5em 0;
        }

        img {
            width: 1.75rem;
            height: 1.75rem;
            margin: 0 0.5rem;
        }
    }

</style>