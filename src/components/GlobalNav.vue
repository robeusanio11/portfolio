<script setup>
import { ref, onMounted, onUnmounted, computed } from 'vue';

const sections = ['projects', 'profile', 'contact'];
const sectionLabels = {
    projects: 'Projects',
    profile: 'Profile',
    contact: 'Contact'
};

const currentIndex = ref(0);

const sectionVisibility = ref({});
let observers = [];

const updateCurrentSection = () => {
    let maxVisibility = 0;
    let mostVisibleIndex = 0;

    sections.forEach((section, index) => {
        const visibility = sectionVisibility.value[section] || 0;
        if (visibility > maxVisibility) {
            maxVisibility = visibility;
            mostVisibleIndex = index;
        }
    });

    currentIndex.value = mostVisibleIndex;
};

const setupIntersectionObserver = () => {
    const options = {
        root: null,
        rootMargin: '0px',
        threshold: [0, 0.1, 0.2, 0.3, 0.4, 0.5, 0.6, 0.7, 0.8, 0.9, 1.0]
    };

    sections.forEach((sectionId) => {
        const element = document.getElementById(sectionId);
        if (!element) return;

        const observer = new IntersectionObserver((entries) => {
            entries.forEach((entry) => {
                sectionVisibility.value[sectionId] = entry.intersectionRatio;
                updateCurrentSection();
            });
        }, options);

        observer.observe(element);
        observers.push(observer);
    });
};

onMounted(() => {
    setupIntersectionObserver();
});

onUnmounted(() => {
    observers.forEach(observer => observer.disconnect());
});

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
    if (currentIndex.value > 0) {
        scrollToSection(currentIndex.value - 1);
    }
};

const goDown = () => {
    if (currentIndex.value < sections.length - 1) {
        scrollToSection(currentIndex.value + 1);
    }
};

const prevSection = computed(() => {
    if (currentIndex.value > 0) {
        return sectionLabels[sections[currentIndex.value - 1]];
    }
    return null;
});

const nextSection = computed(() => {
    if (currentIndex.value < sections.length - 1) {
        return sectionLabels[sections[currentIndex.value + 1]];
    }
    return null;
});
</script>

<template>
    <nav class="global-nav">
        <div class="nav-container">
            <button
                class="nav-arrow up"
                @click="goUp"
                :class="{ disabled: currentIndex === 0 }"
                :disabled="currentIndex === 0"
            >
                <span class="arrow-icon">&#9650;</span>
                <span class="nav-label" v-if="prevSection">
                    {{ prevSection }}
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
                <span class="nav-label" v-if="nextSection">
                    {{ nextSection }}
                </span>
                <span class="arrow-icon">&#9660;</span>
            </button>
        </div>
    </nav>
</template>

<style scoped>
.global-nav {
    position: fixed;
    bottom: 2rem;
    left: 50%;
    transform: translateX(-50%);
    z-index: 1000;
    transition: all 0.4s ease;
}

/* Navigation Styles */
.nav-container {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 2rem;
    padding: 0.75rem 1.5rem;
    background: rgba(0, 0, 0, 0.4);
    backdrop-filter: blur(10px);
    border-radius: 30px;
    border: 1px solid rgba(255, 255, 255, 0.1);
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

/* Tablet */
@media (max-width: 1024px) {
    .global-nav {
        bottom: 1.5rem;
    }

    .nav-container {
        gap: 1.5rem;
        padding: 0.5rem 1rem;
    }

    .nav-label {
        font-size: 0.8rem;
    }

}

/* Mobile */
@media (max-width: 768px) {
    .global-nav {
        bottom: 1rem;
        width: calc(100% - 2rem);
        max-width: 350px;
    }

    .nav-container {
        gap: 1rem;
        padding: 0.4rem 0.75rem;
    }

    .nav-arrow {
        padding: 0.3rem 0.5rem;
        gap: 0.3rem;
    }

    .nav-label {
        font-size: 0.7rem;
    }

    .arrow-icon {
        font-size: 1rem;
    }

    .dot {
        width: 6px;
        height: 6px;
    }

}
</style>
