<template>
    <section id="mainPage">
        <MainSlider />

        <div id="mainIntro">
            <h2>100년 업력의 믿을 수 있는 견고함</h2>
            <p>고객과의 신뢰도 그만큼 견고합니다</p>
        </div>

        <MainTestimony />
    </section> <!-- #mainPage -->

    <ContactUs />
</template> <!-- Template Ends -->

<script setup>
    import MainSlider from '@/components/MainSlider.vue'
    import MainTestimony from '@/components/MainTestimony.vue'
    import ContactUs from '@/components/ContactUs.vue'
</script> <!-- Logic Ends -->

<style lang="scss" scoped>
    #mainPage {
        display: flex;
        flex-flow: column nowrap;
        gap: 100px;
    }

    #mainIntro {
        position: relative;
    }
</style> <!-- Stylesheet Ends -->