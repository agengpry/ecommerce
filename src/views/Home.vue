<template>
	<section class="dark:bg-gray-800 dark:text-gray-100">
		<div class="container flex flex-col justify-center p-6 mx-auto sm:py-12 lg:py-24 lg:flex-row lg:justify-between">
			<div class="flex flex-col justify-center mt-8 ml-8 p-6 text-center rounded-sm lg:max-w-md xl:max-w-lg lg:text-left">
				<h1 class="text-5xl font-bold leadi sm:text-6xl">Destinasi Belanja Online ini Milik mu!
				</h1>
        <i>
				<p class="mt-6 mb-8 text-lg sm:mb-12 font-bold">Jelajahi, Temukan, Belanja
				</p>
        </i>
				<div class="flex flex-col space-y-4 sm:items-center sm:justify-center sm:flex-row sm:space-y-0 sm:space-x-4 lg:justify-start">
          <router-link to="/produk">
					<a rel="noopener noreferrer" href="#" class="px-8 py-3 text-lg font-semibold border rounded dark:border-gray-100">Temukan</a>
        </router-link>
				</div>
			</div>
			<div class="flex items-center justify-center p-6 mt-8 lg:mt-0 h-72 sm:h-80 lg:h-96 xl:h-112 2xl:h-128">
				<img src="https://img.freepik.com/free-vector/online-shopping-concept_52683-63898.jpg?size=626&ext=jpg&ga=GA1.2.250976811.1690423313&semt=ais">
			</div>
		</div>
	</section>
</template>