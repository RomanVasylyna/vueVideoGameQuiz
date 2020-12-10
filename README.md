# myquizapp

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).


import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

Vue Lifecycle Hooks - это функции, который срабатывают в определенный момент жизни
того или иного компонента vue

1) beforeCreate - ивент срабатывает до того как компонент был создан, только после этого мы получаем доступ к data, ивентам и прочему
2) created - срабатывает когда компонент был создан.Он создается, но пока еще не отображается в DOM.
3) beforeMount - Используется редко. Это когда мы хотим что-бы ивент сработал непосредственно перед тем как компонент отрисуется в доме.
4) mounted - на этом этапе дом уже отрисовался и уже есть доступ к коду. Манипулировать дом элементами до mounted невозможно) 
5) beforeUpdate - Код запустится до того как компонент обновится
6) beforeDestroy - Событие срабатывает перед тем как элемент уничтожен
7) destroy - Событие срабатывает в момент уничтожения элемента

Cannot read property 'question' of undefined"
Так происходит потому-что на короткое мгновение, когда компонент отрисовуется, он ждет ответ от АПИ (fetch request) в App.vue

Решение в App.vue в компонент Question добавить v-if="questions.length"

Изучить :
1) v-if (vue conditionals)
2) computed vs method 

