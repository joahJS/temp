<template>
    <subPageHero />
    <div id="" class="web-common-inner common-main-section">
        <BreadCrumbs />

        <section v-if="newsGroup[getId]" id="news-detail">
            <div class="news-content-box">
                <h1>{{newsGroup[getId].title}}</h1>

                <article class="news-date-box">
                    <span>{{newsGroup[getId].site}}</span>
                    <span>{{newsGroup[getId].date}}</span>
                </article>
            </div>
            <div class="news-content-text">
                <p class="linkAdd"> 사이트 주소 : 
                    <a :href="newsGroup[getId]?.linkTo" target="_blank">{{ newsGroup[getId].linkTo }}</a>
                </p>
                <br>
                <img :src="newsGroup[getId].thumImg">

               <br>
               <p>보도내용의 직접적인 외부 게재는 저작권위반에 해당하는 관계로 해당 기사를 열람할 수 있는 링크를 게재합니다.</p>
               <p>상단 링크를 통하여 이동하시면 자세한 내용을 열람하실 수 있습니다.</p>
            </div>

            <div class="mt-5 mb-10 text-center">
                <router-link :to="{name: 'News'}">
                    <button class="all-btn">목록</button>
                </router-link>
            </div>

        </section>


        <!--이전글/다음글-->
         <section id="divMileStone">
         <a href="#" v-if="0 > prevArticle" ref="prevLink">
                <div id="divMilePrev">
                    <p class="prev-next-list">이전 글 <i class="ri-arrow-up-s-line"></i></p>
                    <p data-milestone-prev-title>이전 글이 없습니다.</p>
                </div>
            </a> 
            <a :href="'/news/' + (getId - 1)" v-else ref="prevLink">
                <div id="divMilePrev">
                    <p class="prev-next-list">이전 글 <i class="ri-arrow-up-s-line"></i></p>
                    <p data-milestone-prev-title>{{ newsGroup[getId - 1]?.title }}</p>
                </div>
            </a>
            <a href="#" v-if="dataAmount < nextArticle" ref="nextLink">
                <div id="divMileNext">
                    <p class="prev-next-list next-list">다음 글 <i class="ri-arrow-down-s-line"></i></p>
                    <p data-milestone-next-title v-if="dataAmount < nextArticle">다음 글이 없습니다.</p>
                </div>
            </a> 
            <a :href="'/news/' + (getId + 1)" v-else ref="nextLink" >
                <div id="divMileNext">
                    <p class="prev-next-list next-list">다음 글 <i class="ri-arrow-down-s-line"></i></p>
                    <p data-milestone-next-title>{{ newsGroup[getId + 1]?.title }}</p>
                </div>
            </a>
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

    const newsGroup = ref([

            {
                number: '0',
                site: 'AP신문',
                title: ' 삼표, 일본보다 62% 향상된 ‘자기치유 콘크리트’ 기술 개발',
                date: '2023.03.15',
                thumImg: '/public/images/news/news02.jpg',
                linkTo: 'https://www.apnews.kr/news/articleView.html?idxno=3008791',
            },
            {
                number: '1',
                site: '연합뉴스',
                title: ' 현대 시멘트도 못넘은 고대 로마 초강력 콘크리트 비밀 풀었다',
                date: '2023.01.09',
                thumImg: '/public/images/news/news01.jpg',
                linkTo: 'https://www.yna.co.kr/view/AKR20230109075400009',
            },
        ])

    const dataAmount = parseInt(newsGroup.value.length);
    const nextArticle = parseInt(getId + 2);
    const prevArticle = parseInt(getId - 1);

    const currentArray= newsGroup.value[getId];
    const nextTitle = currentArray["title"];

</script> <!-- Logic Ends -->

<style lang="scss" scoped>

.news-content-box {
    >h1 {
        @apply font-bold py-2;
        
        font-size: var(--font20);
        border-bottom: 1px solid rgba(var(--black), .05);
        line-height: 1.2
    }
}

.news-date-box {
    @apply flex justify-between py-1.5;

    color: rgba(var(--black), .65);
}

.news-content-text {
    @apply py-16;

    min-height: 50vh;
    line-height: 1.4;   
}

.linkAdd {

    @apply font-black;

    > a {
        color:rgba(var(--black), .65);
        font-weight: normal;

        &:hover {
            color:rgba(var(--black), 1);
        }
    }
}

#divMileStone {
    margin-bottom: 5rem
}
#divMilePrev {
    @apply flex items-center px-1;

    border-top:1px solid #ededed ;
    border-bottom:1px solid #ededed ;

    [data-milestone-prev-title]{
        margin-left: 1.5rem;

        &:hover {
            cursor: pointer;
            opacity: .75;
        }
    }
}

#divMileNext {
    @apply flex items-center px-1;

    border-bottom:1px solid #ededed ;

    [data-milestone-next-title]{
        margin-left: 1.5rem;
        
        &:hover{
            cursor: pointer;
            opacity: .75;
        }
    }
}

.prev-next-list {
    @apply py-3 ;

    font-weight: bold;
    flex-shrink: 0;

    &::after {
        content: '';
        border-right:  1px solid rgba(var(--black), .25);
        padding-left: 1rem;
    }

    >i {
        padding-left: 1.5rem;
    }
}
   

</style> <!-- Stylesheet Ends -->