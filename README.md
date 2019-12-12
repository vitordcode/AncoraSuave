# Ancora suave com JavaScript




```
$('html, body').animate({
    scrollTop: targetOffset - 100
}, 500);
```


##### A web é um emaranhado de links. Um tipo de link muito comum é a ancora, que seria um link interno. Basta adicionar ao href uma cerquilha (jogo da velha #) seguida por um nome único ex: href=”#contato” e atribuir um id=”contato” ao elemento na página.

##### Assim ao clicar no link, o scroll automaticamente vai “pular” para onde está o elemento com o id.

##### O objetivo é mudarmos esse pulo, para um scroll suave. Isso garante que o usuário entenda o contexto em que ele está, e em qual local na página esse conteúdo se encontra.


##### Primeiro devemos indicar o tipo de link que ocorrerá o evento, no nosso caso, queremos somente links que forem seguidos por um "#" (ID), assim não teremos problemas com outros tipos de link no nosso Navbar. Ex: link para área de contato, página de login.

```
const menuItems = document.querySelectorAll('.navbar a[href^="#"]');
```
##### Próximo passo é adicionar o evento para cada item ao clicar nomeando a função como preferir, no meu caso "scrollToIdOnClick".  

```
menuItems.forEach(item => {
    item.addEventListener('click', scrollToIdOnClick);
})
```

##### Agora precisamos fazer a referencia entre o "href" e o item, também pegar sua posição atual na pagina atravéz do "offsetTop" 

```
function getScrollTopByHref(element) {
    const id = element.getAttribute('href');
    return document.querySelector(id).offsetTop;
}
```
