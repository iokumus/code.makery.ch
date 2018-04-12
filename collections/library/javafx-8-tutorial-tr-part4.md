---
layout: article
title: "JavaFX 8 Tutorial - 4. Kısım: CSS Biçimlendirme"
date: 2014-04-25 00:00
updated: 2015-05-16 00:00
slug: javafx-8-tutorial/tr/part4
canonical: /library/javafx-8-tutorial/part4/
github: https://github.com/marcojakob/code.makery.ch/edit/master/collections/library/javafx-8-tutorial-tr-part4.md
description: "JavaFX te kullanıcı arayüzünü CSS kullanarak biçimlendirebilirsiniz. Tutorail ın bu kısmında uygulama ikonu da ekleyeceğiz."
image: /assets/library/javafx-8-tutorial/part4/addressapp-part4.png
published: true
prettify: true
comments: true
sidebars:
- header: "Bu serideki makaleler"
  body:
  - text: "Giriş"
    link: /library/javafx-8-tutorial/tr/
    paging: Intro
  - text: "Kısım 1: Scene Builder"
    link: /library/javafx-8-tutorial/tr/part1/
    paging: 1
  - text: "Kısım 2: Model and TableView"
    link: /library/javafx-8-tutorial/tr/part2/
    paging: 2
  - text: "Kısım 3: Kullanıcı ile Etkileşim"
    link: /library/javafx-8-tutorial/tr/part3/
    paging: 3
  - text: "Kısım 4: CSS Biçimlendirme"
    link: /library/javafx-8-tutorial/tr/part4/
    paging: 4
    active: true
  - text: "Kısım 5: Veriyi XML olarak saklama"
    link: /library/javafx-8-tutorial/tr/part5/
    paging: 5
  - text: "Kısım 6: İstatistik Grafiği"
    link: /library/javafx-8-tutorial/tr/part6/
    paging: 6
  - text: "Kısım 7: Yayınlama"
    link: /library/javafx-8-tutorial/tr/part7/
    paging: 7
- header: "Kaynakları İndirin"
  body:
  - text: Eclipse Projesi olarak Kısım 4 <em>(en düşük JDK 8u40 gerektirir)</em>
    link: https://github.com/marcojakob/tutorial-javafx-8/releases/download/v1.1/addressapp-jfx8u40-part-4.zip
    icon-css: fa fa-fw fa-download
languages: 
  header: Languages
  collection: library
  item: javafx-8-tutorial
  part: part4
  active: tr
---

<div class="alert alert-warning">
  <i class="fa fa-language"></i> This page needs a Turkish translation. If you'd like to help out please read <a href="/library/how-to-contribute/" class="alert-link">how to contribute</a>.
</div>

![Screenshot AddressApp Part 4](/assets/library/javafx-8-tutorial/part4/addressapp-part4.png)


## Kısım 4 teki Başlıklar

* **CSS Biçimlendirme**
* Adding an **Application Icon**



*****


## CSS Biçimlendirme 

JavaFX te kullanıcı arayüzünü Kaskat Stil Sayfaları ile (CSS) biçimlendirebilirsiniz. Bu harika birşey! Java uygulamalarının görünümünü özelleştirmek hiç bu kadar kolay olmamıştı.

Bu derste Windows 8 Metro tasarımından ilham alınmış olan bir *DarkTheme* oluşturacağız. Düğmeler için css Pedro Duque Vieira nın blogunu temel almıştır [JMetro - Windows 8 Metro controls on Java](http://pixelduke.wordpress.com/2012/10/23/jmetro-windows-8-controls-on-java/).


### CSS ye aşina olma

JavaFX uygulamanızı biçimlendirmek istiyorsanız CSS hakkında temel bir bilginiz olması gerekir. Başlangıç için iyi bir nokta: [CSS tutorial](http://www.csstutorial.net/).

CSS hakkında daha detaylı JavaFX bilgisi:

* [Skinning JavaFX Applications with CSS](http://docs.oracle.com/javase/8/javafx/user-interface-tutorial/css_tutorial.htm) - Tutorial by Oracle
* [JavaFX CSS Reference](http://docs.oracle.com/javase/8/javafx/api/javafx/scene/doc-files/cssref.html) - Official Reference


### Varsayılan JavaFX CSS

JavaFX 8 deki CSS biçimleri için varsayılan kaynak **`modena.css`** isimli dosyadır. Bu css dosyası Java klasörünüz içerisinde `/jdk1.8.x/jre/lib/ext/jfxrt.jar` bulunan `jfxrt.jar` Java FX jar dosyasıdır. 

`jfxrt.jar` dosyasını çıkartın. `modena.css` dosyasını `com/sun/javafx/scene/control/skin/modena/` altında bulabilirsiniz.

Bu varsayılan biçimlendirme dosyası her zaman Java FX uygulamalarına uygulanır. Özel bir biçimlendirme sayfası ekleyerek `modena.css` deki varsayılan biçimleri geçersiz kılabiliriz.   

<div class="alert alert-info">
**İpucu:** Varsayılan CSS dosyasına gözatmak hangi biçimleri değiştirmeniz gerektiği konusunda fikir verebilir.
</div>


### CSS Biçim Sayfalarını Eklemek

Aşağıdaki `DarkTheme.css` ismindeki CSS dosyasını *view* paketine ekleyin.


##### DarkTheme.css

<pre class="prettyprint lang-css pre-scrollable">
.background {
    -fx-background-color: #1d1d1d;
}

.label {
    -fx-font-size: 11pt;
    -fx-font-family: "Segoe UI Semibold";
    -fx-text-fill: white;
    -fx-opacity: 0.6;
}

.label-bright {
    -fx-font-size: 11pt;
    -fx-font-family: "Segoe UI Semibold";
    -fx-text-fill: white;
    -fx-opacity: 1;
}

.label-header {
    -fx-font-size: 32pt;
    -fx-font-family: "Segoe UI Light";
    -fx-text-fill: white;
    -fx-opacity: 1;
}

.table-view {
    -fx-base: #1d1d1d;
    -fx-control-inner-background: #1d1d1d;
    -fx-background-color: #1d1d1d;
    -fx-table-cell-border-color: transparent;
    -fx-table-header-border-color: transparent;
    -fx-padding: 5;
}

.table-view .column-header-background {
    -fx-background-color: transparent;
}

.table-view .column-header, .table-view .filler {
    -fx-size: 35;
    -fx-border-width: 0 0 1 0;
    -fx-background-color: transparent;
    -fx-border-color: 
        transparent
        transparent
        derive(-fx-base, 80%) 
        transparent;
    -fx-border-insets: 0 10 1 0;
}

.table-view .column-header .label {
    -fx-font-size: 20pt;
    -fx-font-family: "Segoe UI Light";
    -fx-text-fill: white;
    -fx-alignment: center-left;
    -fx-opacity: 1;
}

.table-view:focused .table-row-cell:filled:focused:selected {
    -fx-background-color: -fx-focus-color;
}

.split-pane:horizontal > .split-pane-divider {
    -fx-border-color: transparent #1d1d1d transparent #1d1d1d;
    -fx-background-color: transparent, derive(#1d1d1d,20%);
}

.split-pane {
    -fx-padding: 1 0 0 0;
}

.menu-bar {
    -fx-background-color: derive(#1d1d1d,20%);
}

.context-menu {
    -fx-background-color: derive(#1d1d1d,50%);
}

.menu-bar .label {
    -fx-font-size: 14pt;
    -fx-font-family: "Segoe UI Light";
    -fx-text-fill: white;
    -fx-opacity: 0.9;
}

.menu .left-container {
	-fx-background-color: black;
}

.text-field {
    -fx-font-size: 12pt;
    -fx-font-family: "Segoe UI Semibold";
}

/* 
 * Metro style Push Button
 * Author: Pedro Duque Vieira
 * http://pixelduke.wordpress.com/2012/10/23/jmetro-windows-8-controls-on-java/
 */
.button {
    -fx-padding: 5 22 5 22;   
    -fx-border-color: #e2e2e2;
    -fx-border-width: 2;
    -fx-background-radius: 0;
    -fx-background-color: #1d1d1d;
    -fx-font-family: "Segoe UI", Helvetica, Arial, sans-serif;
    -fx-font-size: 11pt;
    -fx-text-fill: #d8d8d8;
    -fx-background-insets: 0 0 0 0, 0, 1, 2;
}

.button:hover {
    -fx-background-color: #3a3a3a;
}

.button:pressed, .button:default:hover:pressed {
  -fx-background-color: white;
  -fx-text-fill: #1d1d1d;
}

.button:focused {
    -fx-border-color: white, white;
    -fx-border-width: 1, 1;
    -fx-border-style: solid, segments(1, 1);
    -fx-border-radius: 0, 0;
    -fx-border-insets: 1 1 1 1, 0;
}

.button:disabled, .button:default:disabled {
    -fx-opacity: 0.4;
    -fx-background-color: #1d1d1d;
    -fx-text-fill: white;
}

.button:default {
    -fx-background-color: -fx-focus-color;
    -fx-text-fill: #ffffff;
}

.button:default:hover {
    -fx-background-color: derive(-fx-focus-color,30%);
}
</pre>

Şimdi CSS yi Scene e eklememiz gerekli. Bu işi Java koduyla program olarak yapabiliriz ancak fxml dosyalarımıza eklemek için biz Scene Builder kullanacağız: 


#### CSS yi RootLayout.fxml e ekle

1. `RootLayout.fxml` dosyasını Scene Builder da açın. 

2. Hierarchy görünümünde `BorderPane` kökünü seçin. Under *Properties* grup altında stylesheet olarak `DarkTheme.css` dosyasını ekleyin.   
![DarkTheme for RootLayout](/assets/library/javafx-8-tutorial/part4/darktheme-rootlayout.png)


#### CS yi PersonEditDialog.fxml e ekle

1. `PersonEditDialog.fxml` dosyasını Scene Builder da açın. `AnchorPane` kökünü seçin ve *Properties* groupta stylesheet olarak `DarkTheme.css` dosyasını seçin.

2. Arkaplan hala beyaz, bu yüzden `AnchorPane` `background` Style Class ekleyin. 
![Add Style Class](/assets/library/javafx-8-tutorial/part4/darktheme-personeditdialog.png)

3. OK düğmesini seçin ve Properties görünümünde *Default Button* seçin. Bu rengini değiştirecektir ve kullanıcı tarafından *enter* tuşuna basıldığında varsayılan düğme yapacaktır.


#### Attach CSS to PersonOverview.fxml

1. Open the file `PersonOverview.fxml` in Scene Builder. Select the root `AnchorPane` in the *Hierarchy* group. Under properties add the `DarkTheme.css` file as stylesheet.

2. You should already see some changes now: The table and the buttons are black. All class styles `.table-view` and `.button` from `modena.css` apply to the table and buttons. Since we've redefined (and thus overridden) some of those styles in our custom CSS, the new styles are applied automatically.

3. You might need to adjust the size of the buttons so that all text is displayed.

4. Select the right `AnchorPane` that is inside the `SplitPane`.   
![Background Style Select](/assets/library/javafx-8-tutorial/part4/background-style-select.png)   

5. Go to the *Properties* group and select `background` as style class. The background should now turn black.   
![Background Style](/assets/library/javafx-8-tutorial/part4/background-style.png)


#### Labels with Different Style

Right now, all the labels on the right side have the same size. There are already some styles defined in the css file called `.label-header` and `.label-bright` that we'll use to further style the labels.

1. Select the *Person Details* label and add `label-header` as a Style Class.   
![Label Header Style](/assets/library/javafx-8-tutorial/part4/label-header-style.png)

2. To each label in the right column (where the actual person details are displayed), add the css Style Class `label-bright`.   
![Label Bright Style](/assets/library/javafx-8-tutorial/part4/label-bright-style.png)


*****


## Adding an Application Icon

Right now our application just has the default icon in the title bar and taks bar:

![Default Icon](/assets/library/javafx-8-tutorial/part4/default-app-icon.png)

It looks much nicer with a custom icon:

![Custom Icon](/assets/library/javafx-8-tutorial/part4/custom-app-icon.png)


### The Icon File

A possible place to get free icons is [Icon Finder](http://www.iconfinder.com). I downloaded a little [address book icon](https://www.iconfinder.com/icons/86957/address_book_icon#size=32).

Create a (normal) folder inside your AddressApp project called **resources** and a subfolder called **images** in it. Put the icon of your choice inside the images folder. Your folder structure should look something like this now:

![Custom Icon File](/assets/library/javafx-8-tutorial/part4/custom-icon-file.png)


### Set Icon to Scene

To set the icon for our scene add the following line to the `start(...)` method in `MainApp.java`


##### MainApp.java

<pre class="prettyprint lang-java">
this.primaryStage.getIcons().add(new Image("file:resources/images/address_book_32.png"));
</pre>

The whole `start(...)` method should look something like this now:

<pre class="prettyprint lang-java">
public void start(Stage primaryStage) {
    this.primaryStage = primaryStage;
    this.primaryStage.setTitle("AddressApp");

    // Set the application icon.
    this.primaryStage.getIcons().add(new Image("file:resources/images/address_book_32.png"));

    initRootLayout();

    showPersonOverview();
}
</pre>

You can also add an icon to the stage of the person edit dialog, of course.


### What's Next?

In [Tutorial Part 5](/library/javafx-8-tutorial/tr/part5/) we will add XML storage for our data.


##### Some other articles you might find interesting

* [JavaFX Dialogs (official)](/blog/javafx-dialogs-official/)
* [JavaFX Date Picker](/blog/javafx-8-date-picker/)
* [JavaFX Event Handling Examples](/blog/javafx-8-event-handling-examples/)
* [JavaFX TableView Sorting and Filtering](/blog/javafx-8-tableview-sorting-filtering/)
* [JavaFX TableView Cell Renderer](/blog/javafx-8-tableview-cell-renderer/)

