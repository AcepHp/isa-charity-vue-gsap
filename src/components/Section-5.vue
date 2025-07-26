<script setup>
import { citizenData } from '../data/citizenData'
import gsap from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import { nextTick, onMounted } from 'vue'

gsap.registerPlugin(ScrollTrigger)

onMounted(async () => {
    await nextTick()
    const supportCards = document.querySelectorAll('.support-card')
    supportCards.forEach((card) => {
        gsap.from(card, {
            y: 30, // lebih halus, tidak membuat gambar "melompat"
            autoAlpha: 0, // gantikan opacity agar lebih aman
            duration: 1,
            ease: 'power2.out',
            scrollTrigger: {
                trigger: card,
                start: 'top 90%',
                toggleActions: 'play none none reverse',
            },
        })
    })
})
</script>


<template>
    <section class="support-section">
        <div class="support-container">
            <h2 class="support-title">Socially active citizens</h2>
            <div class="support-subtitle">Support us</div>

            <div class="support-grid">
                <main v-for="(member, index) in citizenData" :key="index" class="support-card">
                    <div class="support-content">
                        <div class="support-item">
                            <img :src="member.img" class="support-image" loading="lazy" />
                            <p class="member-name">{{ member.name }}</p>
                            <p class="member-role">{{ member.title }}</p>
                        </div>
                    </div>
                </main>
            </div>
        </div>
    </section>
</template>
