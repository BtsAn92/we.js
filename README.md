# we.js
// ==UserScript==
// @name         Well
// @namespace    http://tampermonkey.net/
// @version      0.1
// @description  try to take over the world!
// @author       You
// @match        https://yandex.ru/*
// @grant        none
// ==/UserScript==
let yandexInput = document.getElementsByName("text")[0];
let button = document.getElementsByClassName("button")[1];
let word = "Гобой";
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
    let links = document.links;
    for(let i=0; i<links.length; i++){
        let link = links[i]
        if(link.href.includes("xn----7sbab5aqcbiddtdj1e1g.xn--p1ai")){
        link.click();
        break;
        }
    }
}
