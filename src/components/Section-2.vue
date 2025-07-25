<script setup>
import gsap from 'gsap'
import { ref, onMounted } from 'vue'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

const itemOne = ref(null)
const itemTwo = ref(null)
const itemThree = ref(null)

onMounted(() => {
    const runScrollAnim = (target) => {
        gsap.fromTo(
            target,
            { x: -100, opacity: 0 },
            {
                x: 0,
                opacity: 1,
                duration: 0.8,
                ease: 'easeInOut',
                scrollTrigger: {
                    trigger: target,
                    start: 'top 80%',
                    end: 'bottom 20%',
                    toggleActions: 'play none none reverse',
                },
            }
        )
    }

    runScrollAnim(itemOne.value)
    runScrollAnim(itemTwo.value)
    runScrollAnim(itemThree.value)
})
</script>

<template>
    <section class="section3">
        <div class="container3">
            <h2>Our projects</h2>
            <div>are very different in terms of priority, scale and complexity of implementation</div>

            <div class="project-wrap" ref="itemOne">
                <div class="project-item">
                    <div class="project-title">Emergency Aid. WAR 2022.</div>
                    <p>
                        providing food and medicine to the shelters and animals which lost their homes and
                        families due to the war
                    </p>
                </div>
            </div>

            <div class="project-wrap2" ref="itemTwo">
                <div class="project-item">
                    <div class="project-title">Non-commercial feed line</div>
                    <p>
                        construction of industrial production base where food for shelters will be produced on a
                        free basis
                    </p>
                </div>
            </div>

            <div class="project-wrap3" ref="itemThree">
                <div class="project-item">
                    <div class="project-title">Education and Control</div>
                    <p>
                        lectures on communication, organisation and coordination of processes, control over the
                        use of aid
                    </p>
                </div>
            </div>
        </div>
    </section>
</template>
