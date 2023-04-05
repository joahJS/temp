<template>
    <subPageHero />
    <div id="" class="web-common-inner common-main-section">
        <BreadCrumbs />

        <section v-if="noticeGroup[getId]" id="notice-detail">
            <div class="noti-title-box">
                <h1>{{noticeGroup[getId].title}}</h1>
                <span>{{noticeGroup[getId].date}}</span>
            </div>
            <div class="noti-content-box">
                <div>
                    <img :src="noticeGroup[getId].thumImg">
                </div>
                <div class="noti-text-box">
                    <p v-for="notitext in noticeGroup[getId]?.textAll" class="notice-text">{{notitext.texts}}</p>
                </div>
            </div>

            <div class="pt-10 text-center">
                <router-link :to="{name: 'Notice'}">
                    <button class="all-btn">목록</button>
                </router-link>
            </div>

        </section>
        
    </div>
    <ContactUs />
</template> <!-- Template Ends -->

<script setup>
    import subPageHero from '@/components/subPageHero.vue'
    import ContactUs from '@/components/ContactUs.vue'
    import BreadCrumbs from '@/components/breadCrumb.vue'

    import { useRoute } from 'vue-router'

    const getParams = useRoute()
    const getId = parseInt(getParams.params.id)

    const noticeGroup = ref([
            {
                number: '0',
                title: 'XXXX콘크리트 10주년 창립기념일',
                date: '2021.12.03',
                thumImg: '/public/images/notice/img03.jpg',
                textAll: [
                   
                    {texts: 'XXXX콘크리트 10주년 창립기념!!'},
                    {texts: '즐거운 추억을 함께한 밤이 되었기를 바랍니다.'},
                ]
            },
            {
                number: '1',
                title: '홈페이지 단장!!',
                date: '2021.12.03',
                thumImg: '/public/images/notice/img02.jpg',
                textAll: [
                    {texts: '새로운 홈페이지가 완성 되었습니다..'},
                    {texts: '많은 관심 부탁드립니다.'},
                ]
            },

        ])
</script> <!-- Logic Ends -->

<style lang="scss" scoped>

.noti-title-box {
    @apply flex flex-col;
    
    >h1 {
        @apply font-bold py-2;
        
        font-size: var(--font20);
        border-bottom: 1px solid rgba(var(--black), .05);
        line-height: 1.2
    }

    >span {
        @apply text-right py-2;
    }
}

.noti-content-box {
    @apply my-20 ;
}

.noti-text-box {
    @apply py-5
}

.notice-text {
    line-height: 1.3;

}


   
</style> <!-- Stylesheet Ends -->