<template>

  <div class="nav">
     <img alt='logo' src='https://www.freepnglogos.com/uploads/rocket-png/rocket-icon-download-png-and-vector-36.png' />
<ul>
    <li>  <a href="https://med-zino.github.io/Portfolio/">CREATOR </a></li>
    <li>  <a href="https://med-zino.github.io/Portfolio/#contact">FEEDBACK </a></li>

   
  </ul></div>
</template>

<script>
export default {

}
</script>

<style scoped>

.nav {

    display: flex;
    align-items: center;
    /* justify-content:center; */
    width: 100%;
    height: 70px;
    border-bottom: 1px solid #30363d;
    align-items: center;
    background-color: #0d1117;
}

ul {
    margin: 0 auto ; /* Center the ul horizontally within .nav */
    padding: 0;
}

img {
    width: 30px;
    /* margin-right: auto; */
    margin-left: 25px;
    filter: invert(100%);
}

li {
    display: inline-block;
    font-weight: 500;
    font-size: 15px;
    color: white;

}
li:nth-child(1) {
    margin-left: -60px;
}

li:nth-child(2) {
    margin-left: 20px;
}

a {
    color: white;
    text-decoration: none;
}

a:hover {
    color: #548ce1;
}

</style>