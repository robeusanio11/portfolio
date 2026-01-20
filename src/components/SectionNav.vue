<script setup>
const props = defineProps({
    currentIndex: {
        type: Number,
        required: true
    }
});

const sections = ['profile', 'projects', 'contact'];
const sectionLabels = {
    profile: 'Profile',
    projects: 'Projects',
    contact: 'Contact'
};

const scrollToSection = (index) => {
    if (index < 0 || index >= sections.length) return;

    const section = document.getElementById(sections[index]);
    if (section) {
        section.scrollIntoView({
            behavior: 'smooth',
            block: 'start'
        });
    }
};

const goUp = () => {
    if (props.currentIndex > 0) {
        scrollToSection(props.currentIndex - 1);
    }
};

const goDown = () => {
    if (props.currentIndex < sections.length - 1) {
        scrollToSection(props.currentIndex + 1);
    }
};
</script>

<template>
    <nav class="section-nav">
        <button
            class="nav-arrow up"
            @click="goUp"
            :class="{ disabled: currentIndex === 0 }"
            :disabled="currentIndex === 0"
        >
            <span class="arrow-icon">&#9650;</span>
            <span class="nav-label" v-if="currentIndex > 0">
                {{ sectionLabels[sections[currentIndex - 1]] }}
            </span>
        </button>

        <div class="section-indicator">
            <span
                v-for="(section, index) in sections"
                :key="section"
                class="dot"
                :class="{ active: currentIndex === index }"
                @click="scrollToSection(index)"
            ></span>
        </div>

        <button
            class="nav-arrow down"
            @click="goDown"
            :class="{ disabled: currentIndex === sections.length - 1 }"
            :disabled="currentIndex === sections.length - 1"
        >
            <span class="nav-label" v-if="currentIndex < sections.length - 1">
                {{ sectionLabels[sections[currentIndex + 1]] }}
            </span>
            <span class="arrow-icon">&#9660;</span>
        </button>
    </nav>
</template>

<style scoped>
.section-nav {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 2rem;
    padding: 0.75rem 1.5rem;
    margin-top: 0;
    /* padding-top: 2rem; */
    /* margin-bottom: 3rem; */
}

.nav-arrow {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    background: transparent;
    border: none;
    color: rgb(200, 200, 200);
    cursor: pointer;
    padding: 0.5rem 1rem;
    border-radius: 20px;
    transition: all 0.3s ease;
}

.nav-arrow:hover:not(.disabled) {
    color: #9263ffff;
    text-shadow:
        0 0 10px #6c2dffff,
        0 0 20px #6c2dffff,
        0 0 30px #6c2dffff;
}

.nav-arrow:hover:not(.disabled) .arrow-icon {
    text-shadow:
        0 0 10px #6c2dffff,
        0 0 20px #6c2dffff,
        0 0 30px #6c2dffff;
}

.nav-arrow.disabled {
    opacity: 0.3;
    cursor: not-allowed;
}

.arrow-icon {
    font-size: 1.2rem;
    transition: all 0.3s ease;
}

.nav-label {
    font-size: 0.9rem;
    font-weight: 400;
    letter-spacing: 0.05em;
    text-transform: uppercase;
}

.section-indicator {
    display: flex;
    gap: 0.5rem;
}

.dot {
    width: 8px;
    height: 8px;
    border-radius: 50%;
    background-color: rgba(255, 255, 255, 0.3);
    cursor: pointer;
    transition: all 0.3s ease;
}

.dot:hover {
    background-color: rgba(255, 255, 255, 0.6);
}

.dot.active {
    background-color: #9263ffff;
    box-shadow:
        0 0 10px #6c2dffff,
        0 0 20px #6c2dffff;
}
</style>
