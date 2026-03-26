---
title: "Vivaldi browser, central tabs"
date: 2026-03-26
draft: false
---

Code to center the Vivaldi browser tabs on the toolbar.

## Step 1: Enable CSS modifications

- Type the following into the address bar: vivaldi://experiments
- Check the “Allow CSS modifications” option

## Step 2: Create the CSS file

Create a folder (e.g., VivaldiCSS) in a safe location outside the Vivaldi installation folder (which is overwritten with every update), such as in Documents. Inside the folder, create a text file named custom.css and paste this code:


```css

#tabs-container.top,
#tabs-container.bottom {
  width: 100% !important;
  display: flex !important;
  justify-content: center !important;
}

#tabs-container.top .resize,
#tabs-container.bottom .resize {
}

#tabs-container.top .tab-strip,
#tabs-container.bottom .tab-strip {
  display: flex !important;
  justify-content: center !important;
  position: relative !important;
}

#tabs-container.top .toolbar.toolbar-tabbar-after.toolbar-large.toolbar-droptarget, #tabs-container.bottom .toolbar.toolbar-tabbar-after.toolbar-large.toolbar-droptarget {
  position: absolute!important;
  width:100px;
    right: 0!important;
}

#tabs-container.bottom .window-buttongroup {
  /*position: absolute!important;
  width:100px;*/
      left: 0 !important;
}
#tabs-container.top .window-buttongroup {
  position: absolute!important;
  width:100px;
      left: 0 !important;
}

#tabs-container.top .tab-position,
#tabs-container.bottom .tab-position {
  position: relative !important;
  transform: none !important;
  left: auto !important;
  --PositionX: 0px !important;
}
```

## Step 3: Link the folder to Vivaldi

- Go to Settings → Appearance
- Scroll down to the “Custom UI changes” section
- Click “Select folder” and choose the VivaldiCSS folder you created

## Step 4: Restart Vivaldi

Close and reopen the browser: the tabs should now appear centered.

---

<img src="/assets/img/vivaldi01.webp">

<img src="/assets/img/vivaldi02.webp" style="background:#E3E3E8">