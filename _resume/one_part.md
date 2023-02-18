---
title: "Резюме"
---
<div class="wrapper" style="background-color:#df91ea"> </div>
## Введение

<span style="color:yellow">█</span>Образование: <br> |  Незаконченное высшее студент 4 курса МАИ «Стрела»
+:---|:---|:---|+
Направление|**Информатика и вычислительная техника**
Английский язык:| **Технический, могу читать документацию.**
Навыки \ технологии|<span style="color:green">█</span> Выше базовых: **`C#`, `ООП`, `SOLID`, `UnityEngine3D`, `Windows`**<br><span style="color:yellow">█</span> Базовые знания: **`HTML`, `CSS`, `PHP`, `Github`, `Qt`, `C++`, `C`**
Почта| **`12312363432@mail.ru`**
Телефон|**`+7ххх9ххх6хх`**


## ↓Краткое резюме↓
В 20(18)-(19) начал погружение в программирование. Пробовал основы С++, остановился на C# в силу хорошей пригодности для обучения.
Часто возвращался к плюсам в ходе обучения в институте. Помимо этого успел ознакомиться с множеством самых разных "около айтишных" тем.
## Об основном Pet-проекте

После изучения основ
<a href="https://metanit.com/sharp/tutorial/" target="_blank">**` C# `**</a>
взялся за изучение 
<a href="https://docs.unity3d.com/ScriptReference/Serializable.html" target="_blank">**` Unity3D `**</a>
  — кроссплатформенной среды разработки приложений.<br>
Имелось желание создать что-то наподобие ММО космических рейнджеров или вакуума-онлайн. В силу неопытности не знал, с чего начать.<br>
Поэтому выбрал популярное в среде новичков решение для клиент-серверного взаимодействия<br>
Остановился на 
<a href="https://www.photonengine.com/" target="_blank">**` Photon-е `**</a>
и спустя время понял, что он мне не подходит. Там используется комнатный матчмейкинг, к тому же сервера — облачные.<br>
Получился по факту мультиплеер для пары человек. Мне же нужен был выделенный сервер с "белым" ip, к которому я мог бы иметь полный доступ.<br><br><br>
<hr width="69%" align="center">↓Получилось как-то так↓<br><br>

<div class="unity-desktop">
      <canvas id="unity-canvas" width=1280 height=720></canvas>
      <div id="unity-loading-bar">
        <div id="unity-logo"></div>
        <div id="unity-progress-bar-empty">
          <div id="unity-progress-bar-full"></div>
        </div>
      </div>
      <div id="unity-warning"> </div>
      <div id="unity-footer">
        //<div id="unity-webgl-logo"></div>
        <div id="unity-fullscreen-button"></div>
        <div id="unity-build-title">Full Screen</div>
      </div>
    </div>
    <script>
      var container = document.querySelector("#unity-container");
      var canvas = document.querySelector("#unity-canvas");
      var loadingBar = document.querySelector("#unity-loading-bar");
      var progressBarFull = document.querySelector("#unity-progress-bar-full");
      var fullscreenButton = document.querySelector("#unity-fullscreen-button");
      var warningBanner = document.querySelector("#unity-warning");

      // Shows a temporary message banner/ribbon for a few seconds, or
      // a permanent error message on top of the canvas if type=='error'.
      // If type=='warning', a yellow highlight color is used.
      // Modify or remove this function to customize the visually presented
      // way that non-critical warnings and error messages are presented to the
      // user.
      function unityShowBanner(msg, type) {
        function updateBannerVisibility() {
          warningBanner.style.display = warningBanner.children.length ? 'block' : 'none';
        }
        var div = document.createElement('div');
        div.innerHTML = msg;
        warningBanner.appendChild(div);
        if (type == 'error') div.style = 'background: red; padding: 10px;';
        else {
          if (type == 'warning') div.style = 'background: yellow; padding: 10px;';
          setTimeout(function() {
            warningBanner.removeChild(div);
            updateBannerVisibility();
          }, 5000);
        }
        updateBannerVisibility();
      }

      var buildUrl = "Build";
      var loaderUrl = buildUrl + "/kep0cuh.github.io.loader.js";
      var config = {
        dataUrl: buildUrl + "/kep0cuh.github.io.data",
        frameworkUrl: buildUrl + "/kep0cuh.github.io.framework.js",
        codeUrl: buildUrl + "/kep0cuh.github.io.wasm",
        streamingAssetsUrl: "StreamingAssets",
        companyName: "DefaultCompany",
        productName: "AnotherStarsSingle",
        productVersion: "1.0",
        showBanner: unityShowBanner,
      };

      // By default Unity keeps WebGL canvas render target size matched with
      // the DOM size of the canvas element (scaled by window.devicePixelRatio)
      // Set this to false if you want to decouple this synchronization from
      // happening inside the engine, and you would instead like to size up
      // the canvas DOM size and WebGL render target sizes yourself.
      // config.matchWebGLToCanvasSize = false;

      if (/iPhone|iPad|iPod|Android/i.test(navigator.userAgent)) {
        // Mobile device style: fill the whole browser client area with the game canvas:

        var meta = document.createElement('meta');
        meta.name = 'viewport';
        meta.content = 'width=device-width, height=device-height, initial-scale=1.0, user-scalable=no, shrink-to-fit=yes';
        document.getElementsByTagName('head')[0].appendChild(meta);
        container.className = "unity-mobile";

        // To lower canvas resolution on mobile devices to gain some
        // performance, uncomment the following line:
        // config.devicePixelRatio = 1;

        canvas.style.width = window.innerWidth + 'px';
        canvas.style.height = window.innerHeight + 'px';

        unityShowBanner('WebGL builds are not supported on mobile devices.');
      } else {
        // Desktop style: Render the game canvas in a window that can be maximized to fullscreen:

        canvas.style.width = "1280px";
        canvas.style.height = "720px";
      }

      loadingBar.style.display = "block";

      var script = document.createElement("script");
      script.src = loaderUrl;
      script.onload = () => {
        createUnityInstance(canvas, config, (progress) => {
          progressBarFull.style.width = 100 * progress + "%";
        }).then((unityInstance) => {
          loadingBar.style.display = "none";
          fullscreenButton.onclick = () => {
            unityInstance.SetFullscreen(1);
          };
        }).catch((message) => {
          alert(message);
        });
      };
      document.body.appendChild(script);
    </script>

<br><br>

<hr width="75%">В 2020 году находился в поисках решения,<br>
которое позволило бы мне сделать не мультиплеер, а реал-таймовую ММО.<br>
<br><br> Особое внимание уделял вопросам, касающимся архитектуры проектов. Поначалу пробовал на системе менеджеров.<br>В итоге остановился на MVC.<br>
К этому моменту времени уже было представление, что мне требуется: сервер на сокетах и клиент к нему. <br>

<br> Сделал простой консольный сервер, опираясь на уроки сайта
<a href="https://metanit.com/sharp/tutorial/" target="_blank">Metanit.</a><br>
                В частности ознакомился с темами:
<a href="https://metanit.com/sharp/net/4.3.php" target="_blank">протокол TCP</a> ,
<a href="https://metanit.com/sharp/net/5.1.php" target="_blank">протокол UDP</a> ,
<a href="https://metanit.com/sharp/net/3.2.php" target="_blank">клиент-серверное приложение на сокетах.</a><br><br>

<img src="/images/КлиентСервер.png"><br>Взаимодействие консольного сервера с консольным клиентом через сокеты.<hr width="65%"><br><br>
По роликам на youtube сделал это  дело многопоточным.<br>
Настроил его на работу в кодировке UTF-8.<br>
<br>В дальнейшем углублялся в тему сериализации данных,в ч.с. с JSON, конвертировал различные типы данных в байты.
<br>Дабы избежать ручной обработки векторов и кватернионов перенес консольный сервер на UnityEngine.<br>
<img src="/images/ЮнитиКлиентСервер.png"><br>Сервер на юнити.<hr width="65%"><br>
Пробовал событийно-ориентированный подход к программированию<br><br>
<img src="/images/События.png"><br>Событие спавна предметов.<hr width="65%"><br>
<hr width="65%">╔=====================================╗<br>╚=====================================╝
</f24px>
</div>

<div align="middle">
            <f24px><hr align="center" width="65%">
                <blue>↓Резюме↓</blue>
                <br><br>Привет!<br> Меня зовут Анатолий Стальнов.<br>
                Я увлекаюсь программированием еще со школы. Все началось со школьного
                <a href="https://yandex.ru/search/?text=КуМир" target="_blank">КуМир-а.</a><br><br>

                Впоследствии немного занимался изучением web-а, выкатывал простой одностраничник на бесплатном хостинге
                <a href="https://ru.000webhost.com/" target="_blank"> 000WebHost</a>.<br>
                Впоследствии на гитхабе скачивал исходники одной довольно интересной браузерной игры <a href="https://2moons.de/" target="_blank"> 2moons.de </a> де-факто xterium, сделанной в виде сайта.<br>
                Опять же размещал все это дело на хостинге. Пробовал копаться в них, немного изменяя баланс.<br>
                Столкнулся с трудностями понимания чужого кода, а также с ограничениями бесплатного тарифа и дальше дело не пошло.<br><br><hr align="center" width="55%">

                В 10 классе пробовал изучать основы С++, но ушел на C#. В 11 классе успел съездить на олимпиаду.<br><br>

                Летом 2019 года взялся за изучение <a href="https://docs.unity3d.com/ScriptReference/Serializable.html" target="_blank">Unity3D</a>  - кроссплатфомернного движка в связке c
                <a href="https://metanit.com/sharp/tutorial/" target="_blank">C# 8.0</a> <br>
                Хотел создать что-то наподобие ММО космических рейнджеров или вакуума-онлайн. В силу неопытности не знал, с чего начать.<br>
                Поэтому выбрал популярное в среде новичков решение для клиент-серверного взаимодействия<br>
                Остановился на <a href="https://www.photonengine.com/" target="_blank"> Photon-е</a> и понял, что он мне не подходит.
                Там используется комнатный матчмейкинг, к тому же сервера - облачные.<br> Получился по факту мультиплеер для пары человек. Мне же нужен был выделенный сервер, к которому я мог бы иметь полный доступ.<br><br><br>
                <hr width="69%">↓В августе 2019 отказался от дальнейшего развития этого проекта. (Билд 2019 года) ↓<br><br>

                <div id="unityContainer" style="width: 1280px; height: 720px; margin: auto"></div><br><br>

                <hr width="75%">С началом учебы осенью все отложил до 2020 года. В начале 2020 года находился в поисках решения,<br>
                которое позволило бы мне сделать не мультиплеер, а реал-таймовую ММО наподобие vacuumonline<br>
                <br><br> Также возникли вопросы, касающиеся архитектуры проектов. Поначалу остановился на самой простой системе менеджеров.<br>
                К 2022 году объединил её с  "примитивной" MVC, +добавил использование событий.<br>
                Незаметно прошел 2020, к 2021 году я уже имел представление, что мне требуется сделать: сервер на сокетах и клиент к нему. <br>

                <br> Весной-летом 2021 консольный сервер был готов, опираясь на уроки сайта
                <a href="https://metanit.com/sharp/tutorial/" target="_blank">Metanit.</a><br>
                В частности ознакомился с темами:
                <a href="https://metanit.com/sharp/net/4.3.php" target="_blank">протокол TCP</a> ,
                <a href="https://metanit.com/sharp/net/5.1.php" target="_blank">протокол UDP</a> ,
                <a href="https://metanit.com/sharp/net/3.2.php" target="_blank">клиент-серверное приложение на сокетах.</a><br><br>

                <img src="/images/КлиентСервер.png"><br>Взаимодействие консольного сервера с консольным клиентом через сокеты.<hr width="65%"><br><br>
                С помощью роликов на youtube сделал это  дело многопоточным.<br>
                Настроил его на работу в кодировке UTF-8.<br>
                Синхронизировал ввод клавиш на клиенте и обработку на сервере.<br>
                <br>Столкнувшись с трудностями ручной обработки векторов и кватернионов перенес консольный сервер на UnityEngine.<br>
                Уже легко далось сделать синхронизацию позиций при некритичном падении производительности.<br>
                добавил спавнеры NPC, предметов. Немного реализовал стрельбу.
                <br> Впоследствии посмотрел новшества C# 10 и платформфы .net 6. Перешел на visual studio 2022.<br>
                Отложил дальнейшую работу над проектом до зимы 2022 года, основные механики по факту сделал.<br>
                Стрельба, движение, спавн, чат, фундамент для системы инвентаря. <br><br>
                <img src="/images/ЮнитиКлиентСервер.png"><br>Сервер на юнити.<hr width="65%"><br>
                Организовал какую-никакую систему событий, опираясь на статьи Habr.<br>
                Она позволила мне создать гибкий контроль со стороны сервера над клиентами, чтобы данные в случае событий отключения\подключения клиента<br>
                было легче обрабатывать \ передавать.<br><br>
                <img src="/images/События.png"><br>Событие спавна предметов.<hr width="65%"><br>
                В заключение, хотелось бы отметить, что сейчас я снова начал смотреть в сторону web-разработки,<br>
                пробежался по php,html,css.<br> Это резюме как раз и сделано после этой пробежки.<br>

                <hr width="65%">╔=====================================╗<br>╚=====================================╝
            </f24px>
        </div>


Ссылки:	

- [Список дистрибутивов Linux (ru.wikipedia.org)](https://ru.wikipedia.org/wiki/%D0%A1%D0%BF%D0%B8%D1%81%D0%BE%D0%BA_%D0%B4%D0%B8%D1%81%D1%82%D1%80%D0%B8%D0%B1%D1%83%D1%82%D0%B8%D0%B2%D0%BE%D0%B2_Linux)
- [Версии Windows (ru.wikipedia.org)](https://ru.wikipedia.org/wiki/Windows#.D0.92.D0.B5.D1.80.D1.81.D0.B8.D0.B8)
- [Wikimedia Traffic Analysis Report - Operating Systems (stats.wikimedia.org)](https://stats.wikimedia.org/wikimedia/squids/SquidReportOperatingSystems.htm)
- [Android базируется на Linux, но что это значит? (rus-linux.net)](http://rus-linux.net/MyLDP/android/android-vs-linux.html)
- [Яндекс](https://ya.ru)
