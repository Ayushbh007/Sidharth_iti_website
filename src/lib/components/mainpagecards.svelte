<script lang="ts">
  export interface Card {
    title: string;
    image: string;
    content: string;
    href: string;
  }

  export let cards: Card[] = [
    {
      title: 'Mission & Objective',
      image: '/images/image_2.jpg',
      content:
        'The scientific developments in various fields have changed the approach to human problems globally. Technical education has become the backbone of national progress, empowering youth with self-reliance and employable skills.',
      href: '#',
    },
    {
      title: 'Schemes Running',
      image: '/images/image_3.jpg',
      content:
        'The Craftsmen Training Scheme was introduced by the Government of India in 1950 to create a steady flow of skilled workers, reduce unemployment, and nurture technical and industrial aptitude among youth.',
      href: '#',
    },
    {
      title: 'Admission Criteria',
      image: '/images/image_4.jpg',
      content:
        'Candidates seeking admission to ITI courses must have passed SS / Matric / ICSE / CBSE or equivalent examination. A minimum of 80% attendance during training is mandatory.',
      href: '#',
    },
  ];
</script>

<!-- MAIN PAGE CARDS -->
<section class="bg-white py-16">
  <div class="mx-auto max-w-7xl px-6 lg:px-8">
    <div class="grid grid-cols-1 gap-10 md:grid-cols-2 lg:grid-cols-3">
      {#each cards as card}
        <article
          class="group flex h-full flex-col overflow-hidden rounded-2xl border border-gray-200 bg-white shadow-sm transition hover:shadow-lg"
        >
          <!-- Image -->
          <div class="aspect-[16/10] overflow-hidden bg-gray-100">
            <img
              src={card.image}
              alt={card.title}
              class="h-full w-full object-cover transition-transform duration-300 group-hover:scale-105"
            />
          </div>

          <!-- Content -->
          <div class="flex flex-1 flex-col p-6">
            <h3 class="mb-3 text-lg font-semibold text-gray-900">
              {card.title}
            </h3>

            <p class="mb-6 text-sm leading-relaxed text-gray-700">
              {card.content}
            </p>

            <div class="mt-auto">
              <a
                href={card.href}
                class="inline-flex items-center text-sm font-medium text-red-600 hover:underline"
              >
                Read More →
              </a>
            </div>
          </div>

          <!-- Accent line -->
          <div class="h-1 w-full bg-red-600"></div>
        </article>
      {/each}
    </div>
  </div>
</section>
