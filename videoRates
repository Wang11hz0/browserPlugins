// ==UserScript==
// @name         新乡医学院学习系统10倍速插件
// @namespace    http://tampermonkey.net/
// @version      0.1
// @description  新乡医学院学习系统10倍速插件，节省时间，无风险，快速拿积分
// @author       ￥whz￥
// @match        http://113.219.200.145:9000/console/index.aspx
// @icon         https://www.google.com/s2/favicons?sz=64&domain=200.145
// @require      https://cdn.jsdelivr.net/npm/jquery@3.5.1/dist/jquery.min.js
// @require      https://cdnjs.cloudflare.com/ajax/libs/layer/2.3/layer.js
// @lisence      MIT
// ==/UserScript==

(function() {
    'use strict';

    function insertRate(){
        var select = $('iframe[id*="layui-layer-iframe"]').contents().find('select[id="selRate"]')
        if(select.length > 0) {
            console.log('aaaaaa',select.children())
            $('<option></option>')
                .css('color', 'red')
                .attr('value', '10').text('10')
                .appendTo(select);

            console.log('aaaaaa',$('#selRate').children())

        }
    }

    let observerIframe = null
    function startObserverIframe(){
        var iframe = document.querySelector('iframe[id*=layui-layer-iframe]')
        // var hasIframe = iframe.body != undefined
        // 未创建时，在创建观察
        // if(observerIframe && !hasIframe){
        //     observerIframe = null
        // }
        // if (hasIframe && !observerIframe){
        //     observerIframe = new MutationObserver(function (records) {
        //         insertRate()
        //     });
        //     observerIframe.observe( iframe.body, {
        //         childList: true,
        //         subtree: true,
        //     });
        // }
        if(iframe){
            iframe.addEventListener('load', () => {
                if(iframe.contentDocument.body.childNodes.length > 0) {
                    console.log('has child nodes');
                    insertRate()
                }
            });
        }

    }

    var oldTime = new Date();
    var MutationObserver = window.MutationObserver || window.WebKitMutationObserver || window.MozMutationObserver;
    var observer = new MutationObserver(function (records) {
        var newTime = new Date();
        if (newTime - oldTime > 200) {
            oldTime = newTime;
            startObserverIframe()
        }
    });
    var option = {
        childList: true,
        subtree: true,
    };
    observer.observe( document.body, option);



})();
