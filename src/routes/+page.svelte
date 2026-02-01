<script lang="ts">
  import Navbar from '$lib/Components/Navbar.svelte';
  import HeroSection from '$lib/Components/HeroSection.svelte';
  import Mainpagecards from '$lib/Components/MainPageCards.svelte';
  import Footer from '$lib/Components/Footer.svelte';
</script>

<Navbar />
<HeroSection />

<!-- NOTICE / INTRO / QUICK LINKS -->
<section class="bg-white py-16">
  <div class="mx-auto max-w-7xl px-6 lg:px-8">
    <div class="grid grid-cols-1 gap-10 lg:grid-cols-12">
      <!-- LEFT: NOTICE BOARD -->
      <aside class="lg:col-span-4">
        <div class="h-full rounded-2xl border border-red-200 bg-white shadow-sm">
          <div class="border-b border-red-200 bg-red-600 px-6 py-4">
            <h2 class="text-lg font-semibold text-white">Notice Board</h2>
          </div>

          <div class="p-6">
            <ul class="space-y-4 text-sm leading-relaxed text-gray-800">
              <li>
                Trainees completing one or two years of training must maintain a minimum of <span
                  class="font-semibold text-red-600">80% attendance</span
                >.
              </li>
              <li>
                Application forms and prospectus are available at the institute office on all
                working days except Sunday.
              </li>
              <li>
                Prospectus fee: <span class="font-semibold">₹150/-</span> payable via demand draft.
              </li>
              <li>Candidates seeking admission must carefully read the admission instructions.</li>
            </ul>

            <a href="#" class="mt-6 inline-block text-sm font-medium text-red-600 hover:underline">
              Read all notices →
            </a>
          </div>
        </div>
      </aside>

      <!-- CENTER: INTRODUCTION -->
      <main class="lg:col-span-5">
        <div class="overflow-hidden rounded-2xl border border-gray-200 bg-white shadow-sm">
          <!-- Image -->
          <div class="aspect-[4/3] w-full overflow-hidden bg-gray-100">
            <img
              src="/images/image_1.jpg"
              alt="Institute Building"
              class="h-full w-full object-cover"
            />
          </div>

          <!-- Content -->
          <div class="p-6">
            <h2 class="mb-3 text-xl font-semibold text-gray-900">Introduction of the Institute</h2>

            <p class="mb-4 text-sm leading-relaxed text-gray-700">
              Siddharth Private Industrial Training Institute is a unit of Mahavir Educational
              Development & Welfare Trust, Chitragopi More, Aurangabad (Bihar). The institute
              operates as an Industrial Training Center (ITC) under private management.
            </p>

            <p class="mb-4 text-sm leading-relaxed text-gray-700">
              Training is offered in multiple trades with one- and two-year programs. On successful
              completion, trainees are awarded
              <span class="font-medium"> National Trade Certificates</span>, recognized across India
              for employment in government and private sectors.
            </p>

            <a
              href="#"
              class="inline-flex items-center text-sm font-medium text-red-600 hover:underline"
            >
              Learn more about the institute →
            </a>
          </div>
        </div>
      </main>

      <!-- RIGHT: QUICK LINKS -->
      <aside class="lg:col-span-3">
        <div class="h-full rounded-2xl border border-gray-200 bg-black shadow-sm">
          <div class="border-b border-white/10 px-6 py-4">
            <h2 class="text-lg font-semibold text-white">Quick Links</h2>
          </div>

          <ul class="divide-y divide-white/10 px-6 py-4 text-sm">
            <li>
              <a href="#" class="block py-3 text-white hover:text-red-400"> ISO Certificates </a>
            </li>
            <li>
              <a href="#" class="block py-3 text-white hover:text-red-400"> About Institute </a>
            </li>
            <li>
              <a href="#" class="block py-3 text-white hover:text-red-400"> Director Message </a>
            </li>
            <li>
              <a href="#" class="block py-3 text-white hover:text-red-400">
                Other Certifications
              </a>
            </li>
            <li>
              <a href="#" class="block py-3 text-white hover:text-red-400"> Schemes Running </a>
            </li>
            <li>
              <a href="#" class="block py-3 text-white hover:text-red-400"> Admission Criteria </a>
            </li>
            <li>
              <a href="#" class="block py-3 text-white hover:text-red-400"> Grievance Redressal </a>
            </li>
          </ul>
        </div>
      </aside>
    </div>
  </div>
</section>
<Mainpagecards />
<Footer />
