<template>
  <nav class="bg-dark border-gray-200 dark:bg-gray-900">
    <div
      class="max-w-screen-xl flex flex-wrap items-center justify-between mx-auto p-4"
    >
      <a href="https://hafidalazhar.vercel.app" class="flex items-center">
        <img
          src="../assets/person.jpeg"
          alt=""
          width="35"
          class="rounded-full mr-2"
        />
        <span
          class="self-center text-3xl font-semibold whitespace-nowrap dark:text-white"
          id="name"
          >Hafid.</span
        >
      </a>
      <button
        data-collapse-toggle="navbar-default"
        type="button"
        class="inline-flex items-center p-2 w-10 h-10 justify-center text-sm text-gray-500 rounded-lg md:hidden hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-gray-200 dark:text-gray-400 dark:hover:bg-gray-700 dark:focus:ring-gray-600"
        aria-controls="navbar-default"
        aria-expanded="false"
      >
        <span class="sr-only">Open main menu</span>
        <svg
          class="w-5 h-5"
          aria-hidden="true"
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 17 14"
        >
          <path
            stroke="currentColor"
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M1 1h15M1 7h15M1 13h15"
          />
        </svg>
      </button>
      <div class="hidden w-full md:block md:w-auto" id="navbar-default">
        <ul
          class="font-medium flex flex-col p-4 md:p-0 mt-4 border border-gray-100 rounded-lg bg-gray-50 md:flex-row md:space-x-8 md:mt-0 md:border-0 md:bg-white dark:bg-gray-800 md:dark:bg-gray-900 dark:border-gray-700"
        >
          <li>
            <a
              href="#"
              class="block mt-2 text-gray-900 rounded hover:bg-gray-100 md:hover:bg-transparent md:border-0 md:hover:text-blue-700 md:p-0 dark:text-white md:dark:hover:text-blue-500 dark:hover:bg-gray-700 dark:hover:text-white md:dark:hover:bg-transparent duration-0 hover:underline decoration-blue-600 decoration-4 underline-offset-8 duration-100"
              >About Me</a
            >
          </li>
          <li>
            <a
              href="#project"
              class="block mt-2 text-gray-900 rounded hover:bg-gray-100 md:hover:bg-transparent md:border-0 md:hover:text-blue-700 md:p-0 dark:text-white md:dark:hover:text-blue-500 dark:hover:bg-gray-700 dark:hover:text-white md:dark:hover:bg-transparent duration-0 hover:underline decoration-blue-600 decoration-4 underline-offset-8 duration-100"
              >Project</a
            >
          </li>
          <li>
            <a
              href="#skills"
              class="block mt-2 text-gray-900 rounded hover:bg-gray-100 md:hover:bg-transparent md:border-0 md:hover:text-blue-700 md:p-0 dark:text-white md:dark:hover:text-blue-500 dark:hover:bg-gray-700 dark:hover:text-white md:dark:hover:bg-transparent duration-0 hover:underline decoration-blue-600 decoration-4 underline-offset-8 duration-100"
              >Skills</a
            >
          </li>
          <li>
            <a
              href="#contact"
              class="block mt-2 text-gray-900 rounded hover:bg-gray-100 md:hover:bg-transparent md:border-0 md:hover:text-blue-700 md:p-0 dark:text-white md:dark:hover:text-blue-500 dark:hover:bg-gray-700 dark:hover:text-white md:dark:hover:bg-transparent duration-0 hover:underline decoration-blue-600 decoration-4 underline-offset-8 duration-100"
              >Contact</a
            >
          </li>
          <li>
            <button
              @click="downloadCV"
              type="button"
              class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 mr-2 mb-2 dark:bg-blue-600 dark:hover:bg-blue-700 focus:outline-none dark:focus:ring-blue-800 font-semibold"
            >
              Download CV
              <i class="bi bi-file-earmark-arrow-down-fill ml-1"></i>
            </button>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  methods: {
    downloadCV() {
      const fileUrl = 'cv_hafid_al_azhar.pdf';
      const fileName = 'CV HAFID AL AZHAR.pdf';

      // Buat objek Blob dari file URL
      fetch(fileUrl)
        .then((response) => response.blob())
        .then((blob) => {
          // Buat object URL dari Blob
          const fileURL = URL.createObjectURL(blob);

          // Buat elemen <a> untuk download
          const downloadLink = document.createElement('a');
          downloadLink.href = fileURL;
          downloadLink.download = fileName;

          // Klik elemen <a> untuk memicu download
          downloadLink.click();

          // Hapus object URL setelah download selesai
          URL.revokeObjectURL(fileURL);
        })
        .catch((error) => {
          console.error('Error downloading CV:', error);
        });
    },
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@600;700&display=swap');

#name {
  font-family: 'Poppins', sans-serif;
  font-weight: bold;
}

.block {
  font-family: 'Poppins', sans-serif;
}

button {
  font-family: 'Poppins', sans-serif;
}
</style>
