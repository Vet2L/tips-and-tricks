# Динамически расширяемый канвас (на все окно) с учетом заданых пропорций

Рендерер расширяется до заданых размеров, а *CSS* стиль все это скейлит.

```
	let ratio = width / height;
    let gr = targetWidth / targetHeight;
    let dr = ratio / gr;
    
    let currentWidth = targetWidth;
    let currentHeight = targetHeight;
    
    if (ratio > gr) {
        currentWidth = Math.floor(currentWidth * dr);
    } else {
        currentHeight = Math.floor(currentHeight / dr);
    }
    
    app.view.style.position = 'absolute';
    app.view.style.left = '0px';
    app.view.style.top = '0px';
    app.view.style.width = `${width}px`;
    app.view.style.height = `${height}px`;
    
    app.renderer.resize(currentWidth, currentHeight);
```

И немного обьяснения:

- **width**, **height** - ширина и высота окна;
- **targetWidth**, **targetHeight** - минимальные размеры, которые должен иметь канвас (1280x720 для примера);
- **currentWidth**, **currentHeight** - новые размеры канваса;
- **app** - [PIXI](https://www.pixijs.com/).Application;
