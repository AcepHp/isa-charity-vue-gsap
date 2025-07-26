<script setup>
import { teamData } from '../data/teamData'
import gsap from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import { nextTick, onMounted } from 'vue'

gsap.registerPlugin(ScrollTrigger)

onMounted(async () => {
    await nextTick()
    const cards = document.querySelectorAll('.team-card')
    cards.forEach((card) => {
        gsap.from(card, {
            y: 100,
            opacity: 0,
            duration: 1,
            ease: 'power2.out',
            scrollTrigger: {
                trigger: card,
                start: 'top 90%',
                end: 'bottom 10%',
                toggleActions: 'play reverse play reverse',
            },
        })
    })
})
</script>

<template>
    <section class="team-section">
        <div class="team-container">
            <h2 class="team-title">Our Team</h2>
            <p class="team-subtitle">
                A group of unique individuals sharing a common goal – to help.
            </p>
            <div class="team-grid">
                <article v-for="(member, index) in teamData" :key="index" class="team-card">
                    <div class="card-content">
                        <img :src="member.img" class="member-photo" alt="Team member" loading="lazy" />
                        <p class="member-name">{{ member.name }}</p>
                        <p class="member-role">{{ member.title }}</p>
                    </div>
                </article>
            </div>
        </div>
    </section>
</template>
