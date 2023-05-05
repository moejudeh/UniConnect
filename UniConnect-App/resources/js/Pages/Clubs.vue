<script setup>
import { Head, Link, usePage } from '@inertiajs/vue3'
import MainNavLayout from '@/Layouts/MainNavLayout.vue'
import ClubBox from '@/Components/Club.vue'
import Magnify from 'vue-material-design-icons/Magnify.vue' 
</script>

<template>
    <Head title="Clubs"/>

    <MainNavLayout>
        <div class = "flex flex-col pt-[85px] items-center  w-full h-[550px] gap-1">
            <div class="w-80% mx-auto pb-1">
                    <img class="h-[350px] w-full rounded-b-xl" src="https://www.linkpicture.com/q/UICHeader.jpg">
            </div>
            <div class="text-[28px] text-center font-extrabold pt-1">Clubs & Organizations at UIC</div>
            <div class="flex items-center justify-center bg-[#EFF2F5] p-1 rounded-full w-[50%]">
                    <Magnify class="p-1" :size="22" fillColor="#64676B"/>
                    <input
                        class="
                            lg:block
                            hidden
                            border-none
                            p-0
                            bg-[#EFF2F5]
                            placeholder-[#64676B]
                            ring-0
                            focus:ring-0
                            w-full
                        "
                        placeholder="Search for clubs in your University..."
                        type="text"
                    >
            </div>
            <div class="text-[28px] text-center font-extrabold pt-1">Top Clubs at UIC</div>
        </div>
        <div class="w-full bg-[#F1F2F5] mt-[30px]">
            <div class=" w-full bg-white h-full">
                <div class="grid grid-flow-row place-items-center grid-cols-3 pt-10">
                    <ClubBox
                        orgName="Assoc. for Computing Machinery (ASM)"
                        orgImage="https://acm.cs.uic.edu/img/logo.png"
                        orgLink="https://acm.cs.uic.edu/"
                    />
                    <ClubBox
                        orgName="Linux User Group (LUG)"
                        orgImage="https://lug.cs.uic.edu/logo.svg"
                        orgLink="https://acm.cs.uic.edu/"
                    />
                    <ClubBox
                        orgName="Women in Computer Science (WiCS)"
                        orgImage="https://wics.students.uic.edu/wp-content/uploads/sites/605/2019/11/calendar-600x365.png"
                        orgLink="https://wics.students.uic.edu/"
                    />
                    <ClubBox
                        orgName="Competitive Gaming Club (CGC)"
                        orgImage="https://static1.campusgroups.com/upload/uic/2020/s3_image_upload_2125713_CGCLogo_Name_829105615.png"
                        orgLink="https://recreation.uic.edu/programs/sport-clubs/competitive-gaming-club/"
                    />
                    <ClubBox
                        orgName="Filipinos in Alliance"
                        orgImage="https://fiauic.org/wp-content/uploads/2021/10/cropped-fiauic_logo_updated-1.png"
                        orgLink="https://fiauic.org/"
                    />
                    <ClubBox
                        orgName="University of Illinois at Chicago"
                        orgImage="https://upload.wikimedia.org/wikipedia/commons/thumb/9/96/University_of_Illinois_at_Chicago_circle_logo.svg/640px-University_of_Illinois_at_Chicago_circle_logo.svg.png"
                        orgLink="https://uic.edu"
                    />

                </div>
            </div>
        </div>
    </MainNavLayout>

    
    
</template>