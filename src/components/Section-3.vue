<script setup>
import { helpData } from '../data/helpData'
import gsap from 'gsap'
import { onMounted } from 'vue'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

onMounted(() => {
    const animatedBlocks = document.querySelectorAll('.help-bg')

    animatedBlocks.forEach((el) => {
        gsap.from(el, {
            y: 100,
            opacity: 0,
            duration: 1,
            ease: 'power2.out',
            scrollTrigger: {
                trigger: el,
                start: 'top 90%',
                end: 'bottom 10%',
                toggleActions: 'play none none reverse',
            },
        })
    })

    const applyBox = document.querySelector('.apply-help')
    if (applyBox) {
        gsap.from(applyBox, {
            x: -100,
            opacity: 0,
            duration: 1,
            ease: 'power2.out',
            scrollTrigger: {
                trigger: applyBox,
                start: 'top 80%',
                end: 'bottom 20%',
                toggleActions: 'play none none reverse',
            },
        })
    }
})
</script>


<template>
    <section class="section4">
        <div class="container4">
            <h2>We want to help</h2>
            <div>
                homeless packs, volunteers, guardians, overstayers, shelters and other organisations
            </div>
            <div class="help-wrap">
                <div class="help-bg" v-for="(title, idx) in helpData" :key="idx">
                    <div class="help-item">
                        <p class="help-title">{{ title }}</p>
                    </div>
                </div>
            </div>
            <div class="apply-help">
                apply for help
                <img src="../assets/images/arrow-1.png" alt="arrow" />
            </div>
        </div>
    </section>
</template>
