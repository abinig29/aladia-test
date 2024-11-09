<template>
  <div class="min-h-screen">
    <section class="lg:bg-[#1C1D1F] relative">
      <ScrollCourseCard :course="course" />
      <div class="max-w-7xl mx-auto px-4 sm:px-16 lg:px-20 py-8 relative">
        <div
          class="absolute shadow-lg lg:block hidden right-[6%] max-w-[360px] top-[50px] z-[100]"
        >
          <CourseCard :course="course" />
        </div>
        <Breadcrumb :items="breadcrumbItems" />
        <div class="block lg:hidden">
          <CourseCard :course="course" />
        </div>
        <div class="grid-cols-3 lg:grid hidden gap-8 relative">
          <div class="col-span-2">
            <CourseInfo :course="course" />
          </div>
        </div>
      </div>
    </section>
    <section class="max-w-7xl mx-auto px-4 sm:px-16 lg:px-20 lg:py-8 py-2">
      <div class="grid lg:grid-cols-3 gap-8 relative">
        <div class="lg:col-span-2">
          <WhatYoullLearn :learningPoints="course.learningPoints" />
          <RelatedTopics :topics="course.relatedTopics" />
          <CourseIncludes :features="course.features" />
          <TopCompanies :companies="course.companies" />
          <CourseContent :content="course.content" />
          <CourseRequirements :requirements="course.requirements" />
          <CourseDescription />
          <RelatedCourses
            :courses="relatedCourses"
            @toggle-wishlist="toggleWishlist"
            @show-more="loadMoreCourses"
          />
          <FrequentlyBoughtTogether
            :courses="frequentlyBoughtTogether"
            :total="35.97"
            :originalTotal="214.97"
          />
          <InstructorProfile :instructor="instructor" />
          <CourseReviews
            :rating="4.7"
            :totalRatings="186"
            :reviews="reviews"
            @helpful="handleReviewHelpful"
          />
          <MoreCoursesByInstructor
            instructorName="Cristian Doru Barin"
            instructorUrl="#"
            :courses="instructorCourses"
            @report-abuse="handleReportAbuse"
          />
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref } from "vue";
import RelatedTopics from "@/components/recommendations/RelatedTopics.vue";
import TopCompanies from "@/components/other/TopCompanies.vue";

const course = ref({
  id: 1,
  title: "Figma for Mobile App Design: Ultimate Edition",
  description:
    "Design Android & iOS mobile apps from zero. Learn from a CEO of an app company & certified Adobe instructor",
  rating: 4.7,
  ratingCount: 186,
  studentCount: 1493,
  instructor: "Cristian Doru Barin",
  lastUpdated: "11/2024",
  language: "English [Auto]",
  price: 10.99,
  originalPrice: 59.99,
  discount: 82,
  relatedTopics: ["Figma", "Design Tools", "Design"],
  requirements: [
    "You don't need any previous experience. You will learn everything you need to know through the course.",
    "You don't need any specific computer. Any laptop or computer will work. No tablets though!",
  ],
  learningPoints: [
    "Create beautiful apps in Figma (a free design program) from scratch, with no previous experience, and add it to your portfolio",
    "Learn about Google Material Design and how to use it. Practical advice that can get you design jobs fast - either as a freelancer or full time",
    "Discover the principles of app design that you can immediately apply. Tips & tricks of professionals for 2023 that will make you look design with confidence",
    "Included: PDF cheat sheets that you can always review, access to my Discord server to chat in real time, all the project files, and more!",
  ],
  features: [
    { icon: "Video", text: "9.5 hours on-demand video" },
    { icon: "FileText", text: "3 articles" },
    { icon: "Download", text: "8 downloadable resources" },
    { icon: "Smartphone", text: "Access on mobile and TV" },
    { icon: "Award", text: "Certificate of completion" },
  ],
  companies: [
    { name: "Nasdaq", logo: "/images//nassaq.png" },
    {
      name: "Volkswagen",
      logo: "/images//Volkswagen.jpg",
    },
    { name: "Box", logo: "/images//box.png" },
    {
      name: "NetApp",
      logo: "/images//NetApp.jpeg",
    },
    {
      name: "Eventbrite",
      logo: "/images//eventbrite.svg",
    },
  ],
  content: {
    totalSections: 7,
    totalLectures: 92,
    totalLength: "9h 39m",
    sections: [
      {
        title: "Introduction",
        lectures: [
          {
            title: "Download all the resources here",
            duration: "00:03",
            type: "resource",
          },
          {
            title: "Design your first app screen",
            duration: "09:14",
            preview: true,
          },
          {
            title: "The most important thing about designing apps",
            duration: "06:41",
            preview: true,
          },
          {
            title: "Figma vs Adobe XD vs Sketch vs Photoshop",
            duration: "07:19",
          },
          {
            title: "Two fundamental skills to have in Figma",
            duration: "04:29",
          },
          { title: "Let's improve our speed", duration: "07:18" },
          {
            title:
              "Here's how apps work and what you need to provide', duration: '06:52' ",
          },
          {
            title: "My honest opinion about animations and no-code",
            duration: "07:01",
            preview: true,
          },
          {
            title:
              "Don't design any mobile app without this!', duration: '06:17' ",
          },
          { title: "Fix this mobile app design", duration: "07:00" },
          { title: "How much $ should you charge?", duration: "04:16" },
          {
            title:
              "Discover Figma's interface & why professionals use it', duration: '07:36' ",
          },
          { title: "Android vs iOS – should you care?", duration: "03:03" },
        ],
        expanded: true,
        duration: "1h 19m",
        lectureCount: 13,
      },
      {
        title: "Flagship App Design Project - Part 1",
        lectures: [],
        expanded: false,
        duration: "2h 26m",
        lectureCount: 23,
      },
      {
        title: "What you need to know about Google Material Design 2&3",
        lectures: [],
        expanded: false,
        duration: "56m",
        lectureCount: 10,
      },
      {
        title: "Typography for Beautiful Mobile Apps",
        lectures: [],
        expanded: false,
        duration: "42m",
        lectureCount: 6,
      },
    ],
  },
});

const relatedCourses = ref([
  {
    id: 1,
    title: "Master Figma for Web Design & Freelancing Learn UI/UX",
    thumbnail: "/images//c1.jpeg",
    rating: 4.7,
    students: 4020,
    totalHours: "12.5 total hours",
    lastUpdated: "10/2024",
    price: 10.99,
    originalPrice: 84.99,
    isWishlisted: false,
    isHighlyRated: true,
  },
  {
    id: 2,
    title: "Responsive UX/UI Design in Figma 1.5h deep dive 2024 UPDATE",
    thumbnail: "/images//c1.jpeg",
    rating: 4.6,
    students: 2849,
    totalHours: "2 total hours",
    lastUpdated: "10/2024",
    price: 10.99,
    originalPrice: 84.99,
    isWishlisted: false,
    isHighlyRated: false,
  },
  {
    id: 3,
    title: "Master Figma for Web Design & Freelancing Learn UI/UX",
    thumbnail: "/images//c1.jpeg",
    rating: 4.7,
    students: 4020,
    totalHours: "12.5 total hours",
    lastUpdated: "10/2024",
    price: 10.99,
    originalPrice: 84.99,
    isWishlisted: false,
    isHighlyRated: false,
  },
  {
    id: 4,
    title: "Responsive UX/UI Design in Figma 1.5h deep dive 2024 UPDATE",
    thumbnail: "/images//c1.jpeg",
    rating: 4.6,
    students: 2849,
    totalHours: "2 total hours",
    lastUpdated: "10/2024",
    price: 10.99,
    originalPrice: 84.99,
    isWishlisted: false,
    isHighlyRated: false,
  },
]);
const frequentlyBoughtTogether = ref([
  {
    id: 1,
    title: "Figma for Mobile App Design: Ultimate Edition",
    instructor: "Cristian Doru Barin",
    thumbnail: "/images//c2.jpeg",
    rating: 4.7,
    ratingCount: "186",
    price: 10.99,
    originalPrice: 84.99,
  },
  {
    id: 2,
    title: "Master Figma for Web Design & Freelancing Learn UI/UX",
    instructor: "Cristian Doru Barin",
    thumbnail: "/images//c2.jpeg",
    rating: 4.7,
    ratingCount: "751",
    badge: "Highest Rated",
    price: 10.99,
    originalPrice: 84.99,
  },
  {
    id: 3,
    title: "Figma UI UX Design Essentials",
    instructor: "Daniel Walter Scott",
    thumbnail: "/images//c2.jpeg",
    rating: 4.7,
    ratingCount: "22,984",
    badge: "Bestseller",
    price: 13.99,
    originalPrice: 84.99,
  },
]);

const reviews = ref([
  {
    id: 1,
    name: "Alexander M.",
    avatar: "/placeholder.svg?height=40&width=40",
    rating: 5,
    timeAgo: "3 months ago",
    content:
      "Very useful course. Especially for total beginners in Figma and design. Almost all my questions were covered. Thank you",
    helpfulCount: 2,
  },
  {
    id: 2,
    name: "Sweta D.",
    avatar: "/placeholder.svg?height=40&width=40",
    rating: 5,
    timeAgo: "4 months ago",
    content: "Amazing explanation for beginner level",
    helpfulCount: 1,
  },
  {
    id: 3,
    name: "Alexander M.",
    avatar: "/placeholder.svg?height=40&width=40",
    rating: 5,
    timeAgo: "3 months ago",
    content:
      "Very useful course. Especially for total beginners in Figma and design. Almost all my questions were covered. Thank you",
    helpfulCount: 2,
  },
  {
    id: 4,
    name: "Sweta D.",
    avatar: "/placeholder.svg?height=40&width=40",
    rating: 5,
    timeAgo: "4 months ago",
    content: "Amazing explanation for beginner level",
    helpfulCount: 1,
  },
]);

const instructor = ref({
  name: "Cristian Doru Barin",
  title: "Adobe Certified Instructor, Web & App Designer, Entrepreneur",
  profileUrl: "#",
  avatar: "/images//teacher.jpg",
  rating: 4.6,
  reviews: 43102,
  students: 291728,
  courses: 14,
  bio: "Chris Barin is a professional web and app designer with nearly 10 years of Photoshop experience. He's also an Adobe Certified Instructor and Certified Photoshop Expert.",
  additionalBio:
    "By being self-taught, he managed to gain the trust of over 270,000 students from all over the world through his Photoshop courses. A staple of his materials is a hands-on, down-to-Earth approach that focuses on getting maximum results with minimal effort.",
});

const instructorCourses = ref([
  {
    id: 1,
    title: "Ultimate Photoshop Training: From Beginner to Pro 2024...",
    instructor: "Cristian Doru Barin",
    thumbnail: "/images//c1.jpeg",
    rating: 4.7,
    ratingCount: "29,721",
    totalHours: "22.5 total hours",
    totalLectures: "221 lectures",
    level: "All Levels",
    price: 10.99,
    originalPrice: 69.99,
    url: "#",
  },
  {
    id: 2,
    title: "Learn Photoshop, Web Design & Profitable...",
    instructor: "Cristian Doru Barin",
    thumbnail: "/images//c1.jpeg",
    rating: 4.8,
    ratingCount: "6,571",
    totalHours: "27 total hours",
    totalLectures: "257 lectures",
    level: "All Levels",
    price: 10.99,
    originalPrice: 69.99,
    url: "#",
  },
  {
    id: 3,
    title: "Graphic Design Masterclass: Design 40+ Projects in...",
    instructor: "Cristian Doru Barin",
    thumbnail: "/images//c1.jpeg",
    rating: 4.4,
    ratingCount: "598",
    totalHours: "16.5 total hours",
    totalLectures: "168 lectures",
    level: "All Levels",
    price: 10.99,
    originalPrice: 69.99,
    url: "#",
  },
]);

function toggleWishlist(courseId) {
  const course = relatedCourses.value.find((c) => c.id === courseId);
  if (course) {
    course.isWishlisted = !course.isWishlisted;
  }
}

function loadMoreCourses() {
  console.log("Loading more courses...");
}

const breadcrumbItems = [
  { name: "Design", href: "#" },
  { name: "Design Tools", href: "#" },
  { name: "Figma", href: "#" },
];

function handleReportAbuse() {
  console.log("Report abuse clicked");
}
</script>
