#BottomSheetBuilder
The support library 23.2.0 introduced a couple of classes to create BottomSheets, so I figured out we should have an easy way to setup a simple BottomSheet with some options.

You can get BottomSheetBuilder on: https://github.com/rubensousa/BottomSheetBuilder

To inflate a View with a BottomSheetBehavior inside a CoordinatorLayout:
``` java
View bottomSheet = new BottomSheetBuilder(context,coordinatorLayout)
        .setMode(BottomSheetBuilder.MODE_GRID)
        .setBackgroundColor(android.R.color.white)
        .setMenu(R.menu.menu_bottom_grid_sheet)
        .createView();
```
The menu resource is used for the grid of options.

The previous code creates a BottomSheet similar to this screen:
![Grid](https://github.com/rubensousa/BottomSheetBuilder/blob/master/screens/sheet-grid.png)

To create a BottomSheetDialog with a custom style:

```java
BottomSheetDialog dialog = new BottomSheetBuilder(context, R.style.AppTheme_BottomSheetDialog)
              .setMode(BottomSheetBuilder.MODE_LIST)
              .setBackgroundColor(android.R.color.white)
              .setMenu(R.menu.menu_bottom_simple_sheet)
              .createDialog();

dialog.show();
```
And the result is something like this:
![List](https://github.com/rubensousa/BottomSheetBuilder/blob/master/screens/sheet-list-submenu.png)