# Data set

>  HTML5에서 데이터를 핸들링하는 방법

```html
<div>
  <ol>
    <li data-option-name="original">1</li>
    <li data-option-name="chilli">2</li>
    <li data-option-name="nacho">3</li>
  </ol>
</div>

<script>
	console.log(document.getElementsByTagName('li')[0].dataset);
  // { optionName: 'original' }
</script>
```

