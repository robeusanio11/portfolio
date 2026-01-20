<script setup>
import { ref, onMounted, onUnmounted, computed } from 'vue';

const sections = ['profile', 'projects', 'contact'];
const sectionLabels = {
    profile: 'Profile',
    projects: 'Projects',
    contact: 'Contact'
};

const currentIndex = ref(0);
const ctaMode = ref(true);
const hasScrolled = ref(false);

// Track which section is most visible
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

// Detect first scroll to exit CTA mode
const handleScroll = () => {
    if (!hasScrolled.value && window.scrollY > 50) {
        hasScrolled.value = true;
        ctaMode.value = false;
    }
};

onMounted(() => {
    setupIntersectionObserver();
    window.addEventListener('scroll', handleScroll, { passive: true });
});

onUnmounted(() => {
    observers.forEach(observer => observer.disconnect());
    window.removeEventListener('scroll', handleScroll);
});

const scrollToSection = (index) => {
    if (index < 0 || index >= sections.length) return;

    const section = document.getElementById(sections[index]);
    if (section) {
        // Exit CTA mode on any navigation click
        ctaMode.value = false;
        hasScrolled.value = true;

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

// In CTA mode on profile, we want to highlight "Projects"
const showCta = computed(() => {
    return ctaMode.value && currentIndex.value === 0;
});
</script>

<template>
    <nav class="global-nav" :class="{ 'cta-mode': showCta }">
        <!-- CTA Mode: Prominent call to action -->
        <div v-if="showCta" class="cta-container">
            <button class="cta-button" @click="scrollToSection(1)">
                <span class="cta-text">View My Projects</span>
                <span class="cta-arrow">&#9660;</span>
            </button>
        </div>

        <!-- Normal Mode: Standard navigation -->
        <div v-else class="nav-container">
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

/* CTA Mode Styles */
.cta-container {
    display: flex;
    justify-content: center;
}

.cta-button {
    display: flex;
    align-items: center;
    gap: 0.75rem;
    background: rgba(146, 99, 255, 0.15);
    border: 1px solid rgba(146, 99, 255, 0.4);
    color: #fff;
    cursor: pointer;
    padding: 0.875rem 1.75rem;
    border-radius: 30px;
    transition: all 0.3s ease;
    animation: pulse-glow 2s ease-in-out infinite;
}

.cta-button:hover {
    background: rgba(146, 99, 255, 0.25);
    border-color: rgba(146, 99, 255, 0.7);
    transform: translateY(-2px);
    box-shadow:
        0 0 20px rgba(108, 45, 255, 0.4),
        0 0 40px rgba(108, 45, 255, 0.2);
}

.cta-text {
    font-size: 1rem;
    font-weight: 500;
    letter-spacing: 0.05em;
    text-transform: uppercase;
}

.cta-arrow {
    font-size: 1rem;
    animation: bounce 1.5s ease-in-out infinite;
}

@keyframes pulse-glow {
    0%, 100% {
        box-shadow:
            0 0 10px rgba(108, 45, 255, 0.3),
            0 0 20px rgba(108, 45, 255, 0.1);
    }
    50% {
        box-shadow:
            0 0 20px rgba(108, 45, 255, 0.5),
            0 0 40px rgba(108, 45, 255, 0.3);
    }
}

@keyframes bounce {
    0%, 100% {
        transform: translateY(0);
    }
    50% {
        transform: translateY(4px);
    }
}

/* Normal Navigation Styles */
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

    .cta-button {
        padding: 0.75rem 1.5rem;
    }

    .cta-text {
        font-size: 0.9rem;
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

    .cta-button {
        padding: 0.625rem 1.25rem;
        gap: 0.5rem;
    }

    .cta-text {
        font-size: 0.8rem;
    }

    .cta-arrow {
        font-size: 0.875rem;
    }
}
</style>
