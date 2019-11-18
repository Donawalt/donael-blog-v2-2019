<template>
    <div class="footer">
        <section>
            <p>© 2019, by  Donaël WALTER</p>
        </section>
        <section>
            <ul>
                <li><a href="https://www.behance.net/donawalt/">behance</a></li>
                <li><a href="https://dribbble.com/donaelwalter/">dribble</a></li>
                <li><a href="https://github.com/Donawalt/">github</a></li>
                <li><a href="https://instagram.com/walt_dona/">instagram</a></li>
                <li><a href="https://www.malt.fr/profile/donawalt/">malt</a></li>
            </ul>
        </section>
    </div>
</template>

<style scoped>
.footer{
    margin-bottom: 0;
    bottom: 0;
    width: 100vw;
    position: absolute;
}
a{
    color:white;
    text-decoration: none;
    transition: 200ms;
}
a:hover{
    transform: scale(1.2);
    border-bottom: 4px solid red;
    transition: 200ms;
}
div{
    height: 64px;
    background-color: #003A65;
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
ul{
    display: flex;
    list-style: none;
}
ul>li{
    margin-left: 24px;
}
</style>