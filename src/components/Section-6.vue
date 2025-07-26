<script setup>
import { onMounted, nextTick } from 'vue'
import gsap from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

onMounted(async () => {
    await nextTick()
    const logos = document.querySelectorAll('.partner-logo')
    logos.forEach((logo) => {
        gsap.from(logo, {
            y: 100,
            opacity: 0,
            duration: 1,
            ease: 'power2.out',
            scrollTrigger: {
                trigger: logo,
                start: 'top 90%',
                end: 'bottom 10%',
                toggleActions: 'play reverse play reverse',
            },
        })
    })
})
</script>

<template>
    <section class="partner-section">
        <div class="partner-container">
            <div class="partner-header">
                <h2 class="partner-title">Our partners</h2>
                <p class="partner-description">
                    are take care of our fund and help us with many questions
                </p>
            </div>

            <div class="partner-grid">
                <div class="partner-logo">
                    <img src="../assets/images/parthner-1.jpg" alt="Partner 1" />
                </div>
                <div class="partner-logo">
                    <img src="../assets/images/parthner-2.png" alt="Partner 2" />
                </div>
                <div class="partner-logo">
                    <img src="../assets/images/parthner-3.png" alt="Partner 3" />
                </div>
                <div class="partner-logo">
                    <img src="../assets/images/parthner-4.png" alt="Partner 4" />
                </div>
                <div class="partner-logo">
                    <img src="../assets/images/parthner-5.png" alt="Partner 5" />
                </div>
                <div class="partner-logo">
                    <img src="../assets/images/parthner-6.jpeg" alt="Partner 6" />
                </div>
            </div>
        </div>
    </section>
</template>
