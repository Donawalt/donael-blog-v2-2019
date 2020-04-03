<template>
    <section class="mobile-menu">
        <nav class="menu">
            <span class="cross">X</span>
            <ul>
                <nuxt-link to="/">
                        <li>home</li>
                    </nuxt-link>
                    <nuxt-link to="/categories">
                        <li>catégories</li>
                    </nuxt-link>
                    <a href="https://www.donaelwalter.com/" traget="_blanck">
                        <li>portfolio</li>
                    </a>
            </ul>
        </nav>
    </section>
</template>

<style scoped>
.mobile-menu{
    position: fixed;
    height: 100vh;
    width: 100vw;
    z-index: 2000;
    background-color: rgba(0, 0, 0, 0.521);
    overflow: hidden;
}
.mobile-menu .menu{
    width: 85vw;
    margin-left: 15vw;
    height: 100%;
    background-color: black;
}
ul{
    margin-left: 0px;
    padding: 0px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    list-style: none;
    height: 100%;
}
a{
    margin-bottom: 10%;
    color: white;
    text-decoration: none;
    font-size: 30px;
}
.cross{
    color: white;
    width: 20px;
    margin-right: 20%;
    margin: 20px;
    z-index: 8000;
    font-weight: bold;
}
</style>