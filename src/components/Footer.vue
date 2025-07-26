<script setup>
import { gsap } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import { ref, onMounted, nextTick } from 'vue'

gsap.registerPlugin(ScrollTrigger)
const animatedFooter = ref(null)

onMounted(async () => {
    await nextTick()
    gsap.fromTo(
        animatedFooter.value,
        { y: 100, opacity: 0 },
        {
            y: 0,
            opacity: 1,
            duration: 1,
            ease: 'power2.out',
            scrollTrigger: {
                trigger: animatedFooter.value,
                start: 'top bottom',
                toggleActions: 'play reverse play reverse',
            },
        }
    )
})
</script>



<template>
    <footer class="footer">
        <div class="footer-left">
            <h2>Contact us</h2>
            <div>Kyiv, Ukraine</div>
            <div>mail@isa.co.ua</div>
            <div class="footer-socials">
                <img src="../assets/images/youtube.svg" alt="YouTube" class="footer-icon" />
                <img src="../assets/images/instagram.svg" alt="Instagram" class="footer-icon" />
                <img src="../assets/images/facebook.svg" alt="Facebook" class="footer-icon" />
                <img src="../assets/images/io.svg" alt="IO" class="footer-icon" />
                <img src="../assets/images/tele.svg" alt="Telegram" class="footer-icon" />
            </div>
        </div>
        <div class="footer-right" ref="animatedFooter">
            <img src="../assets/images/animal-group.svg" alt="Footer Illustration" />
        </div>
    </footer>
</template>
