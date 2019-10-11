<template>
    <div>
        <section>
            <nuxt-link to="/">
                <h2>TB</h2>
            </nuxt-link>
        </section>
        <section>
            <nav>
                <ul>
                    <nuxt-link to="/">
                        <li>home</li>
                    </nuxt-link>
                    <nuxt-link to="/categories">
                        <li>catégories</li>
                    </nuxt-link>
                    <a href="https://www.donaelwalter.com/">
                        <li>portfolio</li>
                    </a>
                </ul>
            </nav>
        </section>
    </div>
</template>

<style scoped>
a{
    color:white;
    text-decoration: none;
    border-bottom: 4px solid rgba(100, 148, 237, 0);
}
a:hover{
    transform: scale(1.1);
    border-bottom: 4px solid red;
    transition: 200ms;
}
div{
    height: 64px;
    background-color: black;
    color: white;
    width: 100vw;
    padding-left: 6.67vw;
    padding-right: 6.67vw;
    display: flex;
    justify-content: space-between;
    align-items: center;
}
section{
    max-height: 30px;
}
nav>ul{
    display: flex;
    list-style: none;
}
nav>ul>a{
    margin-left: 24px;
}
</style>