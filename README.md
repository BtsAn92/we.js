# we.js
/ ==UserScript==
// @name         Well
// @namespace    http://tampermonkey.net/
// @version      0.1
// @description  try to take over the world!
// @author       You
// @match        https://yandex.ru/*
// @grant        none
// ==/UserScript==
function getRandom(min,max){
   return Math.floor( Math.random()*(max-min)+min);
}
let next = document.getElementsByClassName("link_theme_none")
let yandexInput = document.getElementsByName("text")[0];
let button = document.getElementsByClassName("button")[1];
let words = ["Гобой", "Флейта", "Как звучит флейта", "Балалайка", "Фагот", "Скрипка", "Саксофон"];
let word = words[getRandom(0,words.length)];
if (button!=undefined){
    let i = 0;
    let timerId = setInterval(function(){
        yandexInput.value = yandexInput.value + word[i];
        i++;
        if(i == word.length){
           clearInterval(timerId);
            button.click();
        }
    },1000);
}else{
    let linkIsFound = false;
    let links = document.links;
    for(let i=0; i<links.length; i++){
        let link = links[i]
        if(link.href.includes("xn----7sbab5aqcbiddtdj1e1g.xn--p1ai")){
          setTimeout(()=>{link.click();},5000);
          link.click();
          linkIsFound = true;
          break;
        }
    }

    if (!linkIsFound){
         setTimeout(()=>{next.click();},5000)
     }
}
