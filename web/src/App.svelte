<script>
    import Router from "svelte-spa-router";
    import { wrap } from 'svelte-spa-router/wrap'
    import { Spacer, AppBar, Tabs } from "smelte";

    import Home from "./Home.svelte";
    import Route1 from "./Route1.svelte";
    import Upload from "./Upload.svelte";
    import Charts from "./Charts.svelte";
    import VegaCharts from "./VegaCharts.svelte";

    export let name;


    const topMenu = [
        { to: "#/", text: "Home" },
        { to: "#/route1", text: "Route1" },
        { to: "#/upload", text: "Upload" },
        { to: "#/charts", text: "Charts" },
        { to: "#/vega", text: "Vega" },
    ];

    const routes = {
    "/": wrap({
        'component': Home,
        'props':{
            'name': name
        }}),
    "/route1": Route1,
    "/upload": Upload,
    "/charts": Charts,
    "/vega": VegaCharts,
    }

    $: path = document.location.pathname;

</script>

<svelte:head>
    <link
            rel="preconnect"
            crossorigin="anonymous"
            href="https://fonts.gstatic.com"
    />
    <link
            href="https://fonts.googleapis.com/css?family=IBM+Plex+Sans+Condensed:300,400%7CIBM+Plex+Sans:400,600&display=swap"
            rel="stylesheet"
            crossorigin="anonymous"
    />
</svelte:head>

<AppBar  class={i => i.replace('primary-300', 'dark-600')}>
    <a href="." class="px-2 md:px-8 flex items-center">
        <!-- https://freesvg.org/fire-1 -->
        <img src="/fire1.svg" alt="fire logo" width="44" />
        <h6 class="pl-3 text-white tracking-widest font-thin text-lg">
            BEACON
        </h6>
    </a>
    <Spacer />
    <Tabs
        navigation
        items={topMenu}
    />
</AppBar>

<Router {routes} />