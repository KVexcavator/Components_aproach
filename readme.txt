Есть соглашение о именовании через тире, в консоли
document.createElement('random-element').constructor;
С помощью кода JS и пустого класса, расширяющего HTMLElement, мы можем взять желаемое имя элемента и дать ему значение, делать надо с проверкой:
if (!customElements.get('my-custom-tag')) {
customElements.define('my-custom-tag', class extends HTMLElement {});
}
Пример:
<body>
	<wcia-slider></wcia-slider>
</body>
<script>
class Slider extends HTMLElement {
	connectedCallback() {
		alert('hi from Slider');
	}
}
if (!customElements.get('wcia-slider')) {
	customElements.define('wcia-slider', Slider);
}
</script>
-----------------------
innerHTML служит для установки содержимого HTML внутри элемента:
this.innerHTML = '<div class="bg-overlay"></div><div class="thumb"></div>';
подключить к свойству style:
this.style.width = '500px';
--------------------------------
для запроса и выбора его дочерних элементов:
this.querySelector('.bg-overlay').style.width = '100%';
---------------------------------
атрибуты можно встроить в тег компонента:
<wcia-slider backgroundcolor="#0000ff" value="180"></wcia-slider>
Затем мы можем изменить цвет фонового элемента, поменяв «красный» цвет на значение атрибута:
this.querySelector('.bg-overlay').style.backgroundColor = this.getAttribute('backgroundcolor');
------------------------------------
или просто добавить стилей кастомному елементу:
<style>
    wcia-slider { ...
------------------------------------
ипользование полифилов для поддержки в браузерах
npm install @webcomponents/custom-elements
<script src="path/to/custom-elements.min.js"></script>
--------------------------------------
=============================================






















