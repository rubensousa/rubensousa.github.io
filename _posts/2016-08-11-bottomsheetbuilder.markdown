---
layout: post
comments: true
title:  "BottomSheetBuilder"
categories: library
---
The support library 23.2.0 introduced a couple of classes to create BottomSheets, so I figured out we should have an easy way to setup a simple BottomSheet with some options.

<!--break-->

You can get BottomSheetBuilder on:
[https://github.com/rubensousa/BottomSheetBuilder](https://github.com/rubensousa/BottomSheetBuilder)

To inflate a View with a BottomSheetBehavior inside a CoordinatorLayout:

{% highlight java %}
View bottomSheet = new BottomSheetBuilder(context,coordinatorLayout)
        .setMode(BottomSheetBuilder.MODE_GRID)
        .setBackgroundColor(android.R.color.white)
        .setMenu(R.menu.menu_bottom_grid_sheet)
        .createView();
{% endhighlight %}

The menu resource is used for the grid of options.

The previous code creates a BottomSheet similar to this screen:

{: .center}
<img src="https://github.com/rubensousa/BottomSheetBuilder/blob/master/screens/sheet-grid.png?raw=true" width="300">


To create a BottomSheetDialog with a custom style:

{% highlight java %}
BottomSheetDialog dialog = new BottomSheetBuilder(context, R.style.AppTheme_BottomSheetDialog)
              .setMode(BottomSheetBuilder.MODE_LIST)
              .setBackgroundColor(android.R.color.white)
              .setMenu(R.menu.menu_bottom_simple_sheet)
              .createDialog();

dialog.show();
{% endhighlight %}

And the result is something like this:

{: .center}
<img src="https://github.com/rubensousa/BottomSheetBuilder/blob/master/screens/sheet-list-submenu.png?raw=true" width="300">


I recommend the BottomSheetDialog over the inflated view if you want a simple list of options. The dialog gives more focus to them since it darkens the background.