<script setup>
import { ref, onMounted } from 'vue'

import heroImg from '@/assets/img/About/heroImg.png'
import navLogo from '@/assets/navLogo.jpg'
import logoSymbol from '@/assets/img/About/logoSymbol.png'
import infoDesktop from '@/assets/img/About/infoDesktop.png'
import branding from '@/assets/img/About/branding.png'
import achieveImg from '@/assets/img/About/achieveImg.png'
import n68 from '@/assets/img/About/68.png'
import lookingJobs from '@/assets/img/About/lookingJobs.png'

const years = ['2017', '2018', '2019', '2020', '2021'];
const selected = ref(3);
const items = ref([
    {label: "Strategy", icon: logoSymbol},
    {label: "Branding", icon: logoSymbol},
    {label: "Interactive", icon: logoSymbol},
    {label: "Communicate", icon: logoSymbol}
])

const jobs = ref([])
const selectedjob = ref()
 const fetchJobs = async () => {
      try {
        const response = await fetch("https://67ea3f3534bcedd95f62b49f.mockapi.io/it-jobs-NotFound");
        if (!response.ok) throw new Error("Failed to fetch data");
        jobs.value = await response.json();
      } catch (error) {
        console.error(error);
      }
 };

 onMounted(fetchJobs);


</script>

<template>
    <div>
        <section class="mx-auto max-w-6xl my-20"> 
            <div class="hero">
                <div class="grid grid-cols-2">
                    <div class="heroLeft">
                        <h1 class="text-8xl font-bold text-[##232340]">
                            Stand Out
                            from The Crowd.
                        </h1>
                        <p class="w-85 mt-7 font-normal leading-8 text-[#606060]">
                            Agency is a full-service agency, busy designing and building 
                            beautiful digital products, brands, and experiences.
                        </p>
                        <button class="font-bold leading-7 bg-[#5468E7] text-white rounded mt-5 px-5 py-1.5">
                            Recent Work
                        </button>
                    </div>
                    <div >
                        <img :src="heroImg" alt="" class="w-[924px]">
                    </div>
                </div>
            </div>
         </section>
         <section class="bg-[#232340] pb-15">
            <div class="mx-auto max-w-6xl  py-12">
                <div class="grid grid-cols-4">
                    <div>
                         <img class="w-6" :src="logoSymbol" alt="">
                    </div>
                    <div class="col-span-2">
                        <p class="text-[#FFFFFF] text-lg">
                            Who We Are
                        </p>
                        <h2 class="text-[#FFFFFF] text-6xl">
                            We Make Designs that Lead and Inpire.
                        </h2>
                    </div>
                    <div class="mx-45  flex space-x-10">
                        <span class=" pi pi-arrow-left " style="color: white;"></span>
                        <span class="pi pi-arrow-right" style="color: white;"></span>
                    </div>
                </div>

                <div class="mt-10 grid grid-cols-4">
                    <div>
                        <div class=" w-2  ">
                            <div v-for="year in years" :key="year" class="py-10">
                            <div :class="year === '2020' ? 'text-white text-lg' : 'text-[#8B8B8B]'">
                                {{ year }}
                            </div>
                            </div>
                        </div>
                    </div>
                    <div class="col-span-3">
                        <img :src="infoDesktop" alt="">
                    </div>
                    
                </div>

                <div class="mt-10 grid grid-cols-4">
                    <div class="bg-white h-34 w-0.5">
                    </div>

                    <div class="col-span-2">
                        <h3 class="text-3xl text-white font-bold leading-10">
                            A design team building a curated marketplace for UI designers.
                        </h3>
                        <p class="mt-10 text-xl text-[#8B8B8B] font-normal leading-8">
                            4,404 curated design resources to energize your creative workflow. We're a growing family of 334,531 designers and makers from around the world
                        </p>
                        <button class="mt-10 text-white bg-[#5468E7] px-9 py-2 rounded cursor-pointer">
                            Contact Us
                        </button>
                    </div>

                    <div>
                        <img :src="branding" alt="">
                    </div>
                </div>                
            </div>
        </section>
        <section class="mx-auto max-w-6xl my-20">
            <div class="grid grid-cols-4">
                    <div>
                         <img class="w-6" :src="logoSymbol" alt="">
                    </div>
                    <div class="col-span-2">
                        <p class="text-[#5468E7] text-lg">
                            Who We Are
                        </p>
                        <h2 class="text-[#000] text-6xl">
                            We Make Designs that Lead and Inpire.
                        </h2>
                    </div>
                    <div class="mx-45  flex space-x-10">
                        <span class=" pi pi-arrow-left " style="color: #000;"></span>
                        <span class="pi pi-arrow-right" style="color: #000;"></span>
                    </div>
            </div>

            <div class="flex mt-25">
                <div
                    v-for="(item, index) in items" 
                    :key="index"
                    @click="selected = index"
                    class="flex flex-col justify-center items-center  cursor-pointer rounded-2xl"
                    :class="{
                        'w-72 h-95  bg-[#5468E7] text-white' : selected === index,
                        'w-72 h-90 bg-gray-200 text-blue-600' : selected !== index,

                    }"
                >
                <div 
                class="w-16 h-16 rounded-full flex items-center justify-center"
                :class="{
                    'bg-blue-400': selected === index,
                    'bg-gray-200': selected !== index
                }"
                >
                    <img :src="item.icon" alt="" class="w-30" >
                </div>
                    <p class="mt-4 font-semibold text-2xl">{{ item.label }}</p>
            
            </div>
            </div>
            
            
        </section>

         <!-- //achievement -->
         <section class="achievement mt-30">
            <div class="mx-auto max-w-6xl">
                <div class="achievementInfo flex">
                    <div >
                        <img :src="achieveImg" alt="" class="w-300">
                    </div>
                    <div>
                        <div class="flex justify-between ">  
                            <div>
                                <img :src="logoSymbol" alt="" class="w-6" >
                            </div>
                        
                            <p class="text-[#232340] font-semibold leading-6">Achievement</p>
                        </div>
                        <h2 class="mt-10 text-2xl font-bold leading-8">
                            A design team building a curated marketplace for UI designers.
                        </h2>
                        <img :src="n68" alt="" class="mt-20">
                    </div>
                   
                </div>
                

            </div>
         </section>
        
         <!-- Call to action --> 
          <section class="mx-auto max-w-6xl my-20">
            <div :style="{backgroundImage : `url(${lookingJobs})` }" class="relative bg-cover bg-center h-screen">
               <div class="absolute left-1/2 top-30 ">
                   <span class="text-lg text-[#FFFFFF] font-semibold leading-6">
                         Call to action
                   </span>
                   <h1 class="w-95 text-6xl text-[#FFFFFF] font-bold leading-20 tracking-tight">
                         We Are Looking for Talented Designers
                   </h1>
                   <button class="w-50 h-16 mt-10 cursor-pointer bg-white rounded-2xl font-bold leading-6 text-lg text-[#5468E7]">
                      Apply Now
                   </button>
               </div>
            </div>
          </section>

          <!-- Hiring Jobs -->
           <section class=" mx-auto max-w-6xl my-20 mt-20">
            <div class="grid grid-cols-2">
                <div>
                    <div class="hiring flex ">
                        <img :src="logoSymbol" alt="" class="w-6">
                        <p class="text-[#5468E7] text-lg leading-6 font-semibold mx-5">We are hiring</p>
                    </div>
                    <h1 class="mt-10 text-[#232340] font-bold text-8xl tracking-tighter">
                        Jobs
                    </h1>
                    <p class="w-75 mt-10 text-lg leading-8 text-[#606060]">
                        Agency is a full-service agency, busy designing and building beautiful digital products, brands, and experiences.
                    </p>
                    <div class="mt-13 flex items-center space-x-2 cursor-pointer">
                        <span class=" pi pi-arrow-circle-right bg-[#C897E4] text-white rounded-2xl"></span>
                        <p class="text-[#8B8B8B] text-lg font-semibold leading-6">Available jobs</p>
                    </div>
                </div>
                <div>
                    <div v-for="(job, index) in jobs" 
                        :key="index"  
                        @click = "selectedjob = index" 
                        class="mt-5 rounded-2xl"
                        :class = "{
                            'bg-[#232340] text-white' : selectedjob ===index,
                            'bg-[#f2f2f2] ' : selectedjob !== index
                        }"
                    
                    >
                        <h1 
                            class="px-15 pt-10  text-3xl font-bold leading-10 "
                            :class = "{
                                'text-white' : selectedjob === index,
                                'text-[#232340]' : selectedjob !==index
                            }"
                         >{{ job.type }}</h1>
                        <p 
                            class="px-15 pb-5  font-normal text-lg leading-10"
                            :class = "{
                                'text-[#8B8B8B]' : selectedjob === index,
                                'text-[#606060]' : selectedjob !==index
                            }"
                        >{{ job.desc }}</p>
                        <span class="px-15 pb-10 pi pi-arrow-right cursor-pointer"></span>
                    </div>
                </div>
            </div>

           </section>

           <!-- Footer  -->
           <section class="mx-auto max-w-6xl my-20">
                <div>
                    <div class="flex items-center justify-center">
                         <img class='w-40' :src="navLogo" alt="" >
                    </div>
                   <p class="w-6/12 mx-auto text-center text-[#606060] text-lg items-center leading-8">
                        Agency is a full-service agency, busy designing and building beautiful digital products, brands, and experiences.
                   </p>
                   <nav class='w-5/12 mx-auto'>
                        <ul class='flex justify-between '>
                            <li>
                                <a>
                                    About
                                </a>
                            </li>
                             <li>
                                <a>
                                    Work
                                </a>
                            </li>
                             <li>
                                <a>
                                    Services
                                </a>
                            </li>
                             <li>
                                <a>
                                    Jobs
                                </a>
                            </li>
                        </ul>
                   </nav>
                   <hr />
                    <div class="footerButtom">
                        <div class="footerButtom-left text-[#ADADAD] leading-4">
                            © 2020, UI8 LLC.
                        </div>
                         <div class="footerButtom-right text-[#ADADAD] leading-4">
                            <nav>
                                <ul class="flex justify-end">
                                    <li>
                                        <a>
                                            Follow us
                                        </a>
                                    </li>
                                    <li>
                                        <a>
                                            <span class="pi pi-facebook">
                                            </span>
                                        </a>
                                    </li>
                                    <li>
                                        <a>
                                            <span class="pi pi-youtube">
                                            </span>
                                        </a>
                                    </li>
                                     <li>
                                        <a>
                                            <span class="pi pi-instagram">
                                            </span>
                                        </a>
                                    </li>
                                </ul>
                            </nav>
                        </div>
                    </div>
                </div>
           </section>
    </div>
  

    
</template>