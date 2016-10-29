---
layout: post
comments: true
title:  "A different raised button behavior"
categories: sample
---

Since Material Design was introduced, Android has 3 main types of buttons: 

- Floating action buttons
- Raised buttons
- Flat buttons


According to the [spec](https://material.google.com/components/buttons.html), the raised button definition is:

> A typically rectangular material button that lifts and displays ink reactions on press.

But why should it lift? Does your finger work like a magnet? When you press any real button, the force you apply makes the button go down.

<!--break-->

To lift the raised button, Android uses this [StateListAnimator](https://android.googlesource.com/platform/frameworks/base/+/master/core/res/res/anim/button_state_list_anim_material.xml)

From that file, we can see that:

- When the button is pressed, a z-translation (of 4dp) is applied, raising the button from 2dp to 6dp.
- When the button isn't pressed, the elevation is 2dp
- When the button is disabled, the elevation becomes 0dp

What I did was creating a similar one, but instead of applying a positive z-translation and 2dp of elevation, we just set both to 0.
Here's the StateListAnimator: [link](https://github.com/rubensousa/RaiflatButton/blob/master/raiflatbutton/src/main/res/drawable/raiflatbutton_statelistanimator.xml).

Now, you could set this to a button using the **android:stateListAnimator** attribute, but with this approach, you won't be able to use a different elevation, since the value will be hardcoded.

For this reason, I created a library that creates a custom StateListAnimator programmatically using the elevation passed to the view.

You can get it here: [RaiflatButton](https://github.com/rubensousa/RaiflatButton). (Ugly name, I know, but I couldn't figure out a better one).


Now, you can just replace your normal buttons with:
{% highlight xml%}

<com.github.rubensousa.raiflatbutton.RaiflatButton
    android:id="@+id/normalButton"
    style="@style/Base.Widget.AppCompat.Button.Colored"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Colored" />
    
<com.github.rubensousa.raiflatbutton.RaiflatImageButton
    android:id="@+id/imageButton"
    style="@style/Base.Widget.AppCompat.Button"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:src="@drawable/ic_android" />
{% endhighlight %}

Here's a short preview:

<video class='centerVid' width="300" height="533" controls>
    <source src="{{ site.baseurl }}/img/raiflatbutton.webm" type="video/webm">
</video>

So, what do you think? Doesn't this feel more natural for a button?




