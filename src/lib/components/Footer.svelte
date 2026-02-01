<script lang="ts">
  const footerLinks = {
    about: [
      'About Institute',
      'Introduction of the Institute',
      'Administrative Staff',
      'Infrastructure & Workshop',
      'Trade Specific Infrastructure',
      'Court Cases and Status',
      'Electric Power Supply',
      'Fund Status',
      'Rating of Institute by QCI',
      'Other Certifications',
    ],
    students: [
      'Online Practice Test CBT Exam',
      'Records of Trainees',
      'Attendance of Trainees',
      'Progress Report',
      'Overall Results',
      'Details of Certificates Issued',
      'Industry Institute Linkages',
      'Right to Information',
      'Achievements by Trainees',
    ],
    other: [
      'Visitors List',
      'Details of Inspection',
      'State Directorate',
      'DGET & State Govt. Orders',
      'Feedback & Suggestions',
      'Grievance Redressal Mechanism',
      'Certificate Verification',
    ],
    admission: [
      'Schemes Running',
      'Trade',
      'Admission Criteria',
      'Application Format',
      'Information Brochure',
      'Rules & Regulations',
    ],
    facilities: [
      'Placements',
      'Library',
      'Computer Lab',
      'Sports & Recreation',
      'Extra Curricular Activities',
    ],
  };
</script>

<footer class="bg-black text-gray-300">
  <!-- TOP FOOTER -->
  <div class="mx-auto max-w-7xl px-6 py-16 lg:px-8">
    <div class="grid grid-cols-1 gap-10 sm:grid-cols-2 lg:grid-cols-5">
      <!-- ABOUT -->
      <div>
        <h3 class="mb-4 border-b border-red-600 pb-2 text-sm font-semibold uppercase text-white">
          About Us
        </h3>
        <ul class="space-y-2 text-sm">
          {#each footerLinks.about as item}
            <li>
              <a href="#" class="hover:text-red-500">{item}</a>
            </li>
          {/each}
        </ul>
      </div>

      <!-- STUDENTS -->
      <div>
        <h3 class="mb-4 border-b border-red-600 pb-2 text-sm font-semibold uppercase text-white">
          Students Corner
        </h3>
        <ul class="space-y-2 text-sm">
          {#each footerLinks.students as item}
            <li>
              <a href="#" class="hover:text-red-500">{item}</a>
            </li>
          {/each}
        </ul>
      </div>

      <!-- OTHER INFO -->
      <div>
        <h3 class="mb-4 border-b border-red-600 pb-2 text-sm font-semibold uppercase text-white">
          Other Information
        </h3>
        <ul class="space-y-2 text-sm">
          {#each footerLinks.other as item}
            <li>
              <a href="#" class="hover:text-red-500">{item}</a>
            </li>
          {/each}
        </ul>

        <h3
          class="mt-6 mb-4 border-b border-red-600 pb-2 text-sm font-semibold uppercase text-white"
        >
          Faculty
        </h3>
        <ul class="space-y-2 text-sm">
          <li><a href="#" class="hover:text-red-500">Faculty (Technical Staff)</a></li>
          <li><a href="#" class="hover:text-red-500">Attendance of Instructors</a></li>
        </ul>
      </div>

      <!-- ADMISSION -->
      <div>
        <h3 class="mb-4 border-b border-red-600 pb-2 text-sm font-semibold uppercase text-white">
          Admission
        </h3>
        <ul class="space-y-2 text-sm">
          {#each footerLinks.admission as item}
            <li>
              <a href="#" class="hover:text-red-500">{item}</a>
            </li>
          {/each}
        </ul>
      </div>

      <!-- FACILITIES -->
      <div>
        <h3 class="mb-4 border-b border-red-600 pb-2 text-sm font-semibold uppercase text-white">
          Facilities
        </h3>
        <ul class="space-y-2 text-sm">
          {#each footerLinks.facilities as item}
            <li>
              <a href="#" class="hover:text-red-500">{item}</a>
            </li>
          {/each}
        </ul>
      </div>
    </div>
  </div>

  <!-- BOTTOM FOOTER -->
  <div class="border-t border-white/10 bg-black">
    <div
      class="mx-auto flex max-w-7xl flex-col items-center justify-between gap-4 px-6 py-6 text-sm md:flex-row"
    >
      <p class="text-gray-400">
        © Siddharth Private Industrial Training Institute | ISO Certified ITI, Aurangabad, Bihar
      </p>

      <!-- SOCIAL ICONS -->
      <div class="flex items-center gap-4">
        <a href="#" aria-label="Twitter" class="hover:text-red-500">
          <svg class="h-5 w-5 fill-current" viewBox="0 0 24 24">
            <path
              d="M24 4.56c-.89.39-1.85.66-2.85.78a4.94 4.94 0 0 0 2.17-2.72 9.86 9.86 0 0 1-3.13 1.2 4.92 4.92 0 0 0-8.38 4.48A13.96 13.96 0 0 1 1.67 3.15a4.91 4.91 0 0 0 1.52 6.57 4.9 4.9 0 0 1-2.23-.62v.06a4.93 4.93 0 0 0 3.95 4.83 4.93 4.93 0 0 1-2.22.08 4.93 4.93 0 0 0 4.6 3.42A9.88 9.88 0 0 1 0 19.54a13.94 13.94 0 0 0 7.55 2.21c9.05 0 14-7.5 14-14v-.64A10 10 0 0 0 24 4.56z"
            />
          </svg>
        </a>

        <a href="#" aria-label="Facebook" class="hover:text-red-500">
          <svg class="h-5 w-5 fill-current" viewBox="0 0 24 24">
            <path
              d="M22.68 0H1.32C.59 0 0 .6 0 1.33v21.33C0 23.4.59 24 1.32 24h11.5v-9.29H9.69V11.1h3.13V8.41c0-3.1 1.9-4.79 4.66-4.79 1.32 0 2.46.1 2.79.14v3.24h-1.92c-1.5 0-1.8.72-1.8 1.77v2.33h3.6l-.47 3.61h-3.13V24h6.14c.73 0 1.32-.6 1.32-1.34V1.33C24 .6 23.41 0 22.68 0z"
            />
          </svg>
        </a>

        <a href="#" aria-label="YouTube" class="hover:text-red-500">
          <svg class="h-5 w-5 fill-current" viewBox="0 0 24 24">
            <path
              d="M23.5 6.2a3 3 0 0 0-2.1-2.1C19.6 3.6 12 3.6 12 3.6s-7.6 0-9.4.5A3 3 0 0 0 .5 6.2 31.6 31.6 0 0 0 0 12a31.6 31.6 0 0 0 .5 5.8 3 3 0 0 0 2.1 2.1c1.8.5 9.4.5 9.4.5s7.6 0 9.4-.5a3 3 0 0 0 2.1-2.1A31.6 31.6 0 0 0 24 12a31.6 31.6 0 0 0-.5-5.8zM9.6 15.5V8.5L15.8 12l-6.2 3.5z"
            />
          </svg>
        </a>
      </div>
    </div>
  </div>
</footer>
