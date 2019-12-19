<template>
  <div id="app">
    <b-container fluid>
      <b-navbar toggleable="lg">

        <b-navbar-brand href="lco.global">
          <b-img src="https://cdn.lco.global/mainstyle/img/LCO-logo-web.jpg" fluid alt="lco.global"></b-img>
        </b-navbar-brand>

        <b-navbar-nav class="text-left mr-3">
          <h5>Las Cumbres Observatory<br/><small>Science Archive</small></h5>
        </b-navbar-nav>

        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

        <b-collapse id="nav-collapse" is-nav>

          <b-navbar-nav>
            <b-nav-item href="https://lco.global/documentation/archive-documentation/">Documentation</b-nav-item>
            <b-nav-item href="https://archive-api.lco.global/frames/">API</b-nav-item>
            <b-nav-item href="https://lco.global/">Lco.global</b-nav-item>
          </b-navbar-nav>

          <b-navbar-nav class="ml-auto">
            <b-nav-form>
              <b-form-input size="sm" class="mr-sm-2" placeholder="Email" type="email"></b-form-input>
              <b-form-input size="sm" class="mr-sm-2" placeholder="Password" type="password"></b-form-input>
              <b-button size="sm" class="my-2 my-sm-0" type="submit">Login</b-button>
            </b-nav-form>
          </b-navbar-nav>

        </b-collapse>
      </b-navbar>
    </b-container>
    <b-container>
      <router-view/>
    </b-container>
  </div>
</template>
