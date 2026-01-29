<script lang="ts">
  let mobileOpen = false;
  let openMenu: string | null = null;

  const menus = [
    { title: 'Products', items: ['Product A', 'Product B', 'Product C'] },
    { title: 'Solutions', items: ['For Teams', 'For Enterprises', 'For Startups'] },
    { title: 'Company', items: ['About Us', 'Careers', 'Contact'] },
    { title: 'For Hotels', items: ['Hotel CRM', 'Booking Engine', 'Analytics'] },
    { title: 'Pricing', items: ['Plans', 'Compare', 'Custom'] },
    { title: 'Watch Demo', items: ['Live Demo', 'Recorded Demo'] },
  ];

  function toggleMenu(title: string) {
    openMenu = openMenu === title ? null : title;
  }
</script>

<nav class="sticky top-0 z-50 w-full bg-white border-b border-gray-200">
  <div class="w-full">
    <!-- Desktop Navbar (md: 768px+) -->
    <div
      class="hidden md:flex h-16 lg:h-20 xl:h-24 items-center px-3 md:px-4 lg:px-6 xl:px-8 justify-between gap-2 md:gap-3 lg:gap-4"
    >
      <!-- Left: Logo -->
      <div class="flex items-center flex-shrink-0">
        <img src="/logos/logo.png" alt="Engine Logo" class="h-12 md:h-14 lg:h-16 xl:h-20 w-auto" />
      </div>

      <!-- Center: Desktop Menu (first 3 items, rest in More) -->
      <div class="flex items-center gap-1 md:gap-2 lg:gap-3 xl:gap-4 flex-1 justify-center min-w-0">
        <!-- First 3 Menu Items -->
        {#each menus.slice(0, 3) as menu (menu.title)}
          <div
            class="relative hidden sm:block flex-shrink-0"
            on:mouseenter={() => (openMenu = menu.title)}
            on:mouseleave={() => (openMenu = null)}
            role="navigation"
            aria-label="Main navigation"
          >
            <button
              class="flex items-center gap-0.5 md:gap-1 font-medium text-gray-700 hover:text-red-600 transition text-xs md:text-sm lg:text-base whitespace-nowrap"
              aria-expanded={openMenu === menu.title}
              aria-controls="menu-{menu.title}"
            >
              {menu.title}
              <svg
                class="w-3 h-3 md:w-3.5 md:h-3.5 lg:w-4 lg:h-4 flex-shrink-0"
                viewBox="0 0 20 20"
                fill="currentColor"
              >
                <path
                  fill-rule="evenodd"
                  d="M5.23 7.21a.75.75 0 011.06.02L10 10.94l3.71-3.71a.75.75 0 111.06 1.06l-4.24 4.24a.75.75 0 01-1.06 0L5.21 8.29a.75.75 0 01.02-1.08z"
                  clip-rule="evenodd"
                />
              </svg>
            </button>

            {#if openMenu === menu.title}
              <div
                id="menu-{menu.title}"
                class="absolute left-0 mt-2 w-40 md:w-48 lg:w-56 rounded-xl bg-white border border-gray-100 shadow-xl overflow-hidden z-10"
                role="menu"
                aria-labelledby="menu-button-{menu.title}"
              >
                {#each menu.items as item (item)}
                  <a
                    href="#{item.toLowerCase().replace(/\s+/g, '-')}"
                    class="block px-3 md:px-4 py-2 text-xs md:text-sm text-gray-700 hover:bg-gray-50 hover:text-red-600 transition"
                    role="menuitem"
                    tabindex="0"
                  >
                    {item}
                  </a>
                {/each}
              </div>
            {/if}
          </div>
        {/each}

        <!-- More Dropdown -->
        <div
          class="relative flex-shrink-0"
          role="button"
          on:mouseenter={() => (openMenu = 'more')}
          on:mouseleave={() => (openMenu = null)}
        >
          <button
            class="flex items-center gap-0.5 md:gap-1 font-medium text-gray-700 hover:text-red-600 transition text-xs md:text-sm lg:text-base whitespace-nowrap"
            aria-expanded={openMenu === 'more'}
            aria-controls="menu-more"
            on:click={() => (openMenu = openMenu === 'more' ? null : 'more')}
          >
            More
            <svg
              class="w-3 h-3 md:w-3.5 md:h-3.5 lg:w-4 lg:h-4 flex-shrink-0"
              viewBox="0 0 20 20"
              fill="currentColor"
            >
              <path
                fill-rule="evenodd"
                d="M5.23 7.21a.75.75 0 011.06.02L10 10.94l3.71-3.71a.75.75 0 111.06 1.06l-4.24 4.24a.75.75 0 01-1.06 0L5.21 8.29a.75.75 0 01.02-1.08z"
                clip-rule="evenodd"
              />
            </svg>
          </button>

          {#if openMenu === 'more'}
            <div
              id="menu-more"
              class="absolute left-0 mt-2 w-40 md:w-48 lg:w-56 rounded-xl bg-white border border-gray-100 shadow-xl overflow-hidden z-10"
              role="menu"
            >
              {#each menus.slice(3) as menu (menu.title)}
                <div class="border-b border-gray-100 last:border-b-0">
                  <button
                    class="w-full text-left px-3 md:px-4 py-2 font-medium text-gray-700 hover:bg-gray-50 hover:text-red-600 transition text-xs md:text-sm"
                    on:click={() => (openMenu = openMenu === menu.title ? null : menu.title)}
                  >
                    {menu.title}
                  </button>
                  {#if openMenu === menu.title}
                    {#each menu.items as item (item)}
                      <a
                        href="#{item.toLowerCase().replace(/\s+/g, '-')}"
                        class="block px-6 md:px-7 py-2 text-xs md:text-sm text-gray-600 hover:bg-red-50 hover:text-red-600 transition"
                        role="menuitem"
                        tabindex="0"
                      >
                        {item}
                      </a>
                    {/each}
                  {/if}
                </div>
              {/each}
            </div>
          {/if}
        </div>
      </div>

      <!-- Right: Social Icons + Phone -->
      <div class="flex items-center gap-1 md:gap-2 lg:gap-3 xl:gap-4 flex-shrink-0">
        <!-- Social Icons (visible from lg+) -->
        <div class="hidden lg:flex items-center gap-2 lg:gap-3 xl:gap-4">
          <a
            href="https://instagram.com"
            target="_blank"
            aria-label="Instagram"
            class="text-gray-500 hover:text-red-600 transition"
          >
            <svg
              class="w-4 lg:w-5 h-4 lg:h-5 xl:w-6 xl:h-6"
              fill="currentColor"
              viewBox="0 0 24 24"
            >
              <path
                d="M7 2C4.243 2 2 4.243 2 7v10c0 2.757 2.243 5 5 5h10c2.757 0 5-2.243 5-5V7c0-2.757-2.243-5-5-5H7zm10 2a3 3 0 013 3v10a3 3 0 01-3 3H7a3 3 0 01-3-3V7a3 3 0 013-3h10zm-5 3a5 5 0 100 10 5 5 0 000-10zm0 2a3 3 0 110 6 3 3 0 010-6zm5.25-.75a.75.75 0 100 1.5.75.75 0 000-1.5z"
              />
            </svg>
          </a>

          <a
            href="https://youtube.com"
            target="_blank"
            aria-label="YouTube"
            class="text-gray-500 hover:text-red-600 transition"
          >
            <svg
              class="w-4 lg:w-5 h-4 lg:h-5 xl:w-6 xl:h-6"
              fill="currentColor"
              viewBox="0 0 24 24"
            >
              <path
                d="M23.5 6.2a3 3 0 00-2.1-2.1C19.6 3.5 12 3.5 12 3.5s-7.6 0-9.4.6A3 3 0 00.5 6.2 31 31 0 000 12a31 31 0 00.5 5.8 3 3 0 002.1 2.1c1.8.6 9.4.6 9.4.6s7.6 0 9.4-.6a3 3 0 002.1-2.1A31 31 0 0024 12a31 31 0 00-.5-5.8zM9.5 15.5v-7l6 3.5-6 3.5z"
              />
            </svg>
          </a>

          <a
            href="https://t.me"
            target="_blank"
            aria-label="Telegram"
            class="text-gray-500 hover:text-red-600 transition"
          >
            <svg
              class="w-4 lg:w-5 h-4 lg:h-5 xl:w-6 xl:h-6"
              fill="currentColor"
              viewBox="0 0 24 24"
            >
              <path
                d="M22.5 2.5L1.5 11.1c-.9.4-.9 1.6.1 1.9l5.4 1.7 2.1 6.3c.3.9 1.5 1 1.9.2l3-5.1 5.5 4.1c.7.5 1.7.1 1.9-.8l3.6-17.1c.2-1-.7-1.8-1.6-1.4z"
              />
            </svg>
          </a>

          <a
            href="https://wa.me"
            target="_blank"
            aria-label="WhatsApp"
            class="text-gray-500 hover:text-red-600 transition"
          >
            <svg
              class="w-4 lg:w-5 h-4 lg:h-5 xl:w-6 xl:h-6"
              fill="currentColor"
              viewBox="0 0 24 24"
            >
              <path
                d="M12 2a10 10 0 00-8.6 15.1L2 22l5-1.3A10 10 0 1012 2zm0 18a8 8 0 01-4.1-1.1l-.3-.2-3 .8.8-2.9-.2-.3A8 8 0 1112 20zm4.3-5.6c-.2-.1-1.2-.6-1.4-.7-.2-.1-.4-.1-.6.1-.2.2-.6.7-.8.9-.1.2-.3.2-.5.1a6.5 6.5 0 01-3.1-2.7c-.2-.3 0-.4.1-.6l.4-.4c.1-.1.2-.3.3-.4.1-.2 0-.3 0-.4l-.7-1.7c-.2-.4-.4-.4-.6-.4h-.5c-.2 0-.4.1-.6.3-.2.2-.8.8-.8 2s.8 2.4.9 2.6a9.3 9.3 0 004 3.5c.5.2.9.3 1.2.4.5.1.9.1 1.3.1.4-.1 1.2-.5 1.4-.9.2-.4.2-.8.1-.9-.1-.1-.3-.2-.5-.3z"
              />
            </svg>
          </a>

          <a
            href="https://twitter.com"
            target="_blank"
            aria-label="Twitter"
            class="text-gray-500 hover:text-red-600 transition"
          >
            <svg
              class="w-4 lg:w-5 h-4 lg:h-5 xl:w-6 xl:h-6"
              fill="currentColor"
              viewBox="0 0 24 24"
            >
              <path
                d="M23.6 4.6c-.8.4-1.7.6-2.6.8a4.5 4.5 0 001.9-2.5 9 9 0 01-2.9 1.1 4.5 4.5 0 00-7.7 4.1A12.8 12.8 0 013 3.8a4.5 4.5 0 001.4 6 4.4 4.4 0 01-2-.5v.1a4.5 4.5 0 003.6 4.4 4.5 4.5 0 01-2 .1 4.5 4.5 0 004.2 3.1A9 9 0 012 19.5a12.7 12.7 0 006.9 2c8.3 0 12.9-6.9 12.9-12.9v-.6a9.4 9.4 0 002.3-2.4z"
              />
            </svg>
          </a>

          <a
            href="https://facebook.com"
            target="_blank"
            aria-label="Facebook"
            class="text-gray-500 hover:text-red-600 transition"
          >
            <svg
              class="w-4 lg:w-5 h-4 lg:h-5 xl:w-6 xl:h-6"
              fill="currentColor"
              viewBox="0 0 24 24"
            >
              <path
                d="M22.7 0H1.3C.6 0 0 .6 0 1.3v21.3C0 23.4.6 24 1.3 24h11.5v-9.3H9.7v-3.6h3.1V8.4c0-3.1 1.9-4.8 4.7-4.8 1.3 0 2.5.1 2.8.2v3.2h-1.9c-1.5 0-1.8.7-1.8 1.8v2.4h3.6l-.5 3.6h-3.1V24h6.1c.7 0 1.3-.6 1.3-1.3V1.3C24 .6 23.4 0 22.7 0z"
              />
            </svg>
          </a>
        </div>

        <!-- Phone (visible on all md+) -->
        <a
          href="tel:+1234567890"
          class="hidden md:flex items-center gap-1 md:gap-1.5 px-2 md:px-3 py-1.5 rounded-lg hover:bg-red-50 transition flex-shrink-0"
          aria-label="Call Us"
        >
          <svg
            class="w-4 md:w-5 lg:w-5 xl:w-6 h-4 md:h-5 lg:h-5 xl:h-6 text-red-600 flex-shrink-0"
            fill="none"
            stroke="currentColor"
            viewBox="0 0 24 24"
            stroke-width="2"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"
            />
          </svg>
          <span class="hidden xl:block text-xs lg:text-sm font-medium text-gray-700"
            >+1 (234) 567-890</span
          >
        </a>
      </div>
    </div>

    <!-- Mobile Navbar -->
    <div class="md:hidden flex h-16 items-center justify-between px-4">
      <!-- Left: Logo -->
      <div class="flex items-center flex-shrink-0">
        <img src="/logos/logo.png" alt="Engine Logo" class="h-12 w-auto" />
      </div>

      <!-- Right: Mobile Menu Button -->
      <button
        class="text-2xl text-gray-700 hover:text-red-600 transition"
        on:click={() => (mobileOpen = !mobileOpen)}
        aria-label="Toggle menu"
      >
        {mobileOpen ? '✕' : '☰'}
      </button>
    </div>
  </div>

  <!-- Mobile Menu -->
  {#if mobileOpen}
    <div class="md:hidden bg-white border-t border-gray-200 px-4 py-4 space-y-3">
      <!-- Mobile Menu Items -->
      {#each menus as menu (menu.title)}
        <div>
          <button
            class="w-full flex justify-between items-center font-medium text-gray-800 py-2 hover:text-red-600 transition"
            on:click={() => toggleMenu(menu.title)}
          >
            {menu.title}
            <span class="text-lg">{openMenu === menu.title ? '−' : '+'}</span>
          </button>

          {#if openMenu === menu.title}
            <div class="mt-2 ml-4 space-y-2">
              {#each menu.items as item (item)}
                <a
                  href="#{item.toLowerCase().replace(/\s+/g, '-')}"
                  class="block text-sm text-gray-600 hover:text-red-600 py-1 transition"
                  on:click={() => (mobileOpen = false)}
                >
                  {item}
                </a>
              {/each}
            </div>
          {/if}
        </div>
      {/each}

      <!-- Mobile Social Icons & Phone -->
      <div class="border-t border-gray-200 pt-4 mt-4">
        <!-- Phone Section -->
        <a
          href="tel:+1234567890"
          class="flex items-center gap-3 py-3 px-2 rounded-lg hover:bg-gray-50 transition mb-3"
        >
          <svg
            class="w-5 h-5 text-red-600 flex-shrink-0"
            fill="none"
            stroke="currentColor"
            viewBox="0 0 24 24"
            stroke-width="2"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"
            />
          </svg>
          <span class="text-sm font-medium text-gray-700">+1 (234) 567-890</span>
        </a>

        <!-- Social Icons -->
        <div class="flex items-center gap-4 justify-center py-3">
          <a
            href="https://instagram.com"
            target="_blank"
            aria-label="Instagram"
            class="text-gray-500 hover:text-red-600 transition"
          >
            <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
              <path
                d="M7 2C4.243 2 2 4.243 2 7v10c0 2.757 2.243 5 5 5h10c2.757 0 5-2.243 5-5V7c0-2.757-2.243-5-5-5H7zm10 2a3 3 0 013 3v10a3 3 0 01-3 3H7a3 3 0 01-3-3V7a3 3 0 013-3h10zm-5 3a5 5 0 100 10 5 5 0 000-10zm0 2a3 3 0 110 6 3 3 0 010-6zm5.25-.75a.75.75 0 100 1.5.75.75 0 000-1.5z"
              />
            </svg>
          </a>
          <a
            href="https://youtube.com"
            target="_blank"
            aria-label="YouTube"
            class="text-gray-500 hover:text-red-600 transition"
          >
            <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
              <path
                d="M23.5 6.2a3 3 0 00-2.1-2.1C19.6 3.5 12 3.5 12 3.5s-7.6 0-9.4.6A3 3 0 00.5 6.2 31 31 0 000 12a31 31 0 00.5 5.8 3 3 0 002.1 2.1c1.8.6 9.4.6 9.4.6s7.6 0 9.4-.6a3 3 0 002.1-2.1A31 31 0 0024 12a31 31 0 00-.5-5.8zM9.5 15.5v-7l6 3.5-6 3.5z"
              />
            </svg>
          </a>
          <a
            href="https://t.me"
            target="_blank"
            aria-label="Telegram"
            class="text-gray-500 hover:text-red-600 transition"
          >
            <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
              <path
                d="M22.5 2.5L1.5 11.1c-.9.4-.9 1.6.1 1.9l5.4 1.7 2.1 6.3c.3.9 1.5 1 1.9.2l3-5.1 5.5 4.1c.7.5 1.7.1 1.9-.8l3.6-17.1c.2-1-.7-1.8-1.6-1.4z"
              />
            </svg>
          </a>
          <a
            href="https://wa.me"
            target="_blank"
            aria-label="WhatsApp"
            class="text-gray-500 hover:text-red-600 transition"
          >
            <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
              <path
                d="M12 2a10 10 0 00-8.6 15.1L2 22l5-1.3A10 10 0 1012 2zm0 18a8 8 0 01-4.1-1.1l-.3-.2-3 .8.8-2.9-.2-.3A8 8 0 1112 20zm4.3-5.6c-.2-.1-1.2-.6-1.4-.7-.2-.1-.4-.1-.6.1-.2.2-.6.7-.8.9-.1.2-.3.2-.5.1a6.5 6.5 0 01-3.1-2.7c-.2-.3 0-.4.1-.6l.4-.4c.1-.1.2-.3.3-.4.1-.2 0-.3 0-.4l-.7-1.7c-.2-.4-.4-.4-.6-.4h-.5c-.2 0-.4.1-.6.3-.2.2-.8.8-.8 2s.8 2.4.9 2.6a9.3 9.3 0 004 3.5c.5.2.9.3 1.2.4.5.1.9.1 1.3.1.4-.1 1.2-.5 1.4-.9.2-.4.2-.8.1-.9-.1-.1-.3-.2-.5-.3z"
              />
            </svg>
          </a>
          <a
            href="https://twitter.com"
            target="_blank"
            aria-label="Twitter"
            class="text-gray-500 hover:text-red-600 transition"
          >
            <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
              <path
                d="M23.6 4.6c-.8.4-1.7.6-2.6.8a4.5 4.5 0 001.9-2.5 9 9 0 01-2.9 1.1 4.5 4.5 0 00-7.7 4.1A12.8 12.8 0 013 3.8a4.5 4.5 0 001.4 6 4.4 4.4 0 01-2-.5v.1a4.5 4.5 0 003.6 4.4 4.5 4.5 0 01-2 .1 4.5 4.5 0 004.2 3.1A9 9 0 012 19.5a12.7 12.7 0 006.9 2c8.3 0 12.9-6.9 12.9-12.9v-.6a9.4 9.4 0 002.3-2.4z"
              />
            </svg>
          </a>
          <a
            href="https://facebook.com"
            target="_blank"
            aria-label="Facebook"
            class="text-gray-500 hover:text-red-600 transition"
          >
            <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
              <path
                d="M22.7 0H1.3C.6 0 0 .6 0 1.3v21.3C0 23.4.6 24 1.3 24h11.5v-9.3H9.7v-3.6h3.1V8.4c0-3.1 1.9-4.8 4.7-4.8 1.3 0 2.5.1 2.8.2v3.2h-1.9c-1.5 0-1.8.7-1.8 1.8v2.4h3.6l-.5 3.6h-3.1V24h6.1c.7 0 1.3-.6 1.3-1.3V1.3C24 .6 23.4 0 22.7 0z"
              />
            </svg>
          </a>
        </div>
      </div>
    </div>
  {/if}
</nav>
