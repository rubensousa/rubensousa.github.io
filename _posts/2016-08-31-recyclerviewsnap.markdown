---
layout: post
comments: true
title:  "RecyclerView snapping with SnapHelper"
categories: sample
---

The 24.2.0 version of the support library introduced two new classes 
([SnapHelper](https://developer.android.com/reference/android/support/v7/widget/SnapHelper.html)
 and [LinearSnapHelper](https://developer.android.com/reference/android/support/v7/widget/LinearSnapHelper.html)) 
 that should be used to handle snapping in a RecyclerView.

You've probably already noticed this in the Google Play app:

{: .center}
<img src="{{ site.baseurl }}/img/snap_googleplay.gif" width="300">

As you can see, the RecyclerView snaps to the first item in the adapter.

<!--break-->

If you use the default LinearSnapHelper, **you can only snap to the center.**

The only code needed is:

{% highlight java%}

SnapHelper snapHelper = new LinearSnapHelper();
snapHelper.attachToRecyclerView(recyclerView);
{% endhighlight %}

This produces the following result:

{: .center}
<img src="{{ site.baseurl }}/img/snap_center.gif" width="300">

To replicate the Google Play behavior, we need to override the **calculateDistanceToFinalSnap**
and **findSnapView** methods of the LinearSnapHelper to find the start view and calculate the distance needed to snap it to the correct position.

To make this easier to do, I created a **GravitySnapHelper** that supports snapping in 4 directions (start, top, end, bottom).

If you want the same behavior as the Google Play app, now you only need to change the previous code to:
{% highlight java%}
SnapHelper snapHelper = new GravitySnapHelper(Gravity.START); 
snapHelper.attachToRecyclerView(startRecyclerView);
{% endhighlight %}

Make sure you set the appropriate orientation in the LayoutManager too:

{% highlight java%}
// HORIZONTAL for Gravity START/END and VERTICAL for TOP/BOTTOM
recyclerView.setLayoutManager(new LinearLayoutManager(this,
LinearLayoutManager.HORIZONTAL, false));
{% endhighlight %}

Here's a complete example:

{: .center}
<img src="{{ site.baseurl }}/img/snap_final.gif" width="300">


This sample is available on my Github:
[https://github.com/rubensousa/RecyclerViewSnap/](https://github.com/rubensousa/RecyclerViewSnap/)






