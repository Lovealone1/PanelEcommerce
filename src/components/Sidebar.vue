<template>
    <nav class="navbar navbar-vertical fixed-start navbar-expand-md navbar-light" id="sidebar">
      <div class="container-fluid">
    
        <!-- Toggler -->
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#sidebarCollapse" aria-controls="sidebarCollapse" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
    
        <!-- Brand -->
        <a class="navbar-brand" href="./colaborador">
          <img src="/assets/img/logo.svg" class="navbar-brand-img mx-auto" alt="...">
        </a>
    
        <!-- User (xs) -->
        <div class="navbar-user d-md-none">
    
          <!-- Dropdown -->
          <div class="dropdown">
    
            <!-- Toggle -->
            <a href="#" id="sidebarIcon" class="dropdown-toggle" role="button" data-bs-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
              <div class="avatar avatar-sm avatar-online">
                <img src="/assets/img/avatar-1.jpg" class="avatar-img rounded-circle" alt="..." >
              </div>
            </a>
    
            <!-- Menu -->
            <div class="dropdown-menu dropdown-menu-end" aria-labelledby="sidebarIcon">
              <a href="./profile-posts.html" class="dropdown-item">Perfil</a>
              <a href="./account-general.html" class="dropdown-item">Configuraciones</a>
              <hr class="dropdown-divider">
              <a href="./" class="dropdown-item">Cerrar Sesión</a>
            </div>
    
          </div>
    
        </div>
    
            <li class="nav-item">
              <router-link to="/colaborador" class="nav-link" active-class="active">
                <i class="fe fe-user"></i> Colaboradores
              </router-link>
            </li>
          <hr class="navbar-divider my-3">

          <h6 class="navbar-heading">
              Control
          </h6>
          <ul class="navbar-nav mb-md-4">
            <li class="nav-item">
              <router-link to="/producto" class="nav-link" active-class="active">
                <i class="fe fe-shopping-cart"></i> Productos
              </router-link>
            </li>
            <li class="nav-item">
              <router-link to="/categorias" class="nav-link" active-class="active">
                <i class="fe fe-tag"></i> Categorias
              </router-link>
            </li>
            <li class="nav-item">
              <router-link to="/ingreso" class="nav-link" active-class="active">
                <i class="fe fe-folder"></i> Ingreso de productos
              </router-link>
            </li>
            <li class="nav-item">
              <router-link to="/ventas" class="nav-link" active-class="active">
                <i class="fe fe-shopping-bag"></i> Ventas
              </router-link>
            </li>
          </ul>
          <!-- Push content down -->
          <div class="mt-auto"></div>
    
    
        </div> <!-- / .navbar-collapse -->
    
    </nav>
</template>
  
  <script>
  export default {
    name: 'Sidebar',
  }
  </script>
