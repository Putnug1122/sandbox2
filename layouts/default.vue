<template>
  <div id="app">
    <div class="main-wrapper">
      <div class="navbar-bg"></div>
      <partials-navbar />
      <partials-sidebar />

      <!-- Main Content -->
      <div class="main-content">
        <section class="section">
          <div class="section-header">
            <h1>Aplikasi Buku</h1>
          </div>

          <div class="section-body">
            <Nuxt />
          </div>
        </section>
      </div>
      <partials-footer />
    </div>
  </div>
</template>
