<script setup>
import { onMounted, ref } from 'vue'
import gsap from 'gsap'
import ScrollTrigger from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

const imageA = ref(null)
const imageB = ref(null)
const titleText = ref(null)
const subtitleText = ref(null)
const socialIcons = ref(null)
const arrowBounce = ref(null)

onMounted(() => {
    gsap.set([imageA.value, imageB.value], { y: -200, opacity: 0 })

    const loopAnim = gsap.timeline({ repeat: -1 })

    loopAnim
        .to(imageA.value, { y: 0, opacity: 1, duration: 0.3 })
        .to(imageA.value, { y: 100, opacity: 0, duration: 0.3, delay: 1 })
        .to(imageB.value, { y: 0, opacity: 1, duration: 0.3 })
        .to(imageB.value, { y: 100, opacity: 0, duration: 0.3, delay: 1 })

    gsap.set(titleText.value, { x: 200, opacity: 0 })
    gsap.set(subtitleText.value, { y: 100, opacity: 0 })
    gsap.set(socialIcons.value, { y: 100, opacity: 0 })
    gsap.set(arrowBounce.value, { y: 50, opacity: 0 })

    gsap.to(titleText.value, {
        scrollTrigger: {
            trigger: titleText.value,
            start: 'top 80%',
            end: 'bottom 20%',
            toggleActions: 'play reverse play reverse'
        },
        x: 0,
        opacity: 1,
        duration: 1,
        ease: 'power3.out'
    })

    gsap.to(subtitleText.value, {
        scrollTrigger: {
            trigger: subtitleText.value,
            start: 'top 90%',
            end: 'bottom 10%',
            toggleActions: 'play reverse play reverse'
        },
        y: 0,
        opacity: 1,
        duration: 1,
        delay: 0.3,
        ease: 'power3.out'
    })

    gsap.to(socialIcons.value, {
        scrollTrigger: {
            trigger: socialIcons.value,
            start: 'top 90%',
            end: 'bottom 10%',
            toggleActions: 'play reverse play reverse'
        },
        y: 0,
        opacity: 1,
        duration: 1,
        delay: 0.3,
        ease: 'power3.out'
    })

    gsap.to(arrowBounce.value, {
        opacity: 1,
        y: 0,
        duration: 1,
        delay: 2.5,
        ease: 'power3.out',
        onComplete: () => {
            gsap.to(arrowBounce.value, {
                y: -10,
                repeat: -1,
                yoyo: true,
                duration: 0.8,
                ease: 'power1.inOut'
            })
        }
    })
})
</script>

<template>
    <header class="hero-section">
        <div class="hero-wrapper">
            <div>
                <button class="btn-donate">donate</button>
            </div>
            <div>
                <button class="btn-webflow">
                    <img src="../assets/images/webflow-badge.svg" alt="Webflow Badge" />
                    Made in Webflow
                </button>
            </div>
            <div class="hero-main">
                <div class="img-wrapper">
                    <img ref="imageA" src="../assets/images/animal-1.svg" alt="hero" class="animal animal-a" loading="lazy" />
                    <img ref="imageB" src="../assets/images/animal-1.svg" alt="hero" class="animal animal-b" loading="lazy" />
                </div>
                <h1 class="title-text" ref="titleText">
                    Innovative <br />
                    Solutions <br />
                    for <br />
                    Animals
                </h1>
            </div>
            <div class="subtitle-text" ref="subtitleText">charity organization</div>
        </div>

        <div class="social-group" ref="socialIcons">
            <img src="../assets/images/youtube.svg" alt="YouTube" class="icon-social" />
            <img src="../assets/images/instagram.svg" alt="Instagram" class="icon-social" />
            <img src="../assets/images/facebook.svg" alt="Facebook" class="icon-social" />
            <img src="../assets/images/io.svg" alt="IO" class="icon-social" />
            <img src="../assets/images/tele.svg" alt="Telegram" class="icon-social" />
        </div>

        <div class="arrow-bounce" ref="arrowBounce">
            <img src="../assets/images/arrow.png" alt="Scroll Down Arrow" />
        </div>
    </header>
</template>
