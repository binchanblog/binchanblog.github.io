---
layout: post
title: Work with WinForms ScrollBar Control
categories:
  - Coding
tags:
  - scrollbar
  - C#
  - winform
published: true
---

## HScrollBar設定

{% highlight js %}
/// <summary> 最小値 </summary>
private const Int32 _MIN = 0;
/// <summary> 最大値 </summary>
private const Int32 _MAX = 100;

scroll.Minimum = _MIN;
scroll.Maximum = _MAX + (scroll.LargeChange - 1);

Int32 min = scroll.Minimum;
Int32 max = scroll.Maximum - (scroll.LargeChange - 1);
{% endhighlight %}

## HScrollBarのValueを直接指定

{% highlight js %}
/// <summary>
/// HScrollBarのValueを直接指定
/// </summary>
/// <param name="aScrollBar">HScrollBarコントロール</param>
/// <param name="aValue">Valueプロパティにセットする値</param>
public static void HScrollBar_SetValue(HScrollBar aScrollBar, Int32 aValue)
{
	if (aScrollBar.Minimum <= aValue && aValue <= aScrollBar.Maximum - (aScrollBar.LargeChange - 1))
	{
		aScrollBar.Value = aValue;
	}
	else if (aValue < aScrollBar.Minimum)
	{
		aScrollBar.Value = aScrollBar.Minimum;
	}
	else if (aScrollBar.Maximum - (aScrollBar.LargeChange - 1) < aValue)
	{
		aScrollBar.Value = aScrollBar.Maximum - (aScrollBar.LargeChange - 1);
	}
	else
	{
		// DO NOTHING
	}
}
{% endhighlight %}

## HScrollBarの現在位置をマウスホイールの回転数分移動

{% highlight js %}
/// <summary>
/// HScrollBarの現在位置をマウスホイールの回転数分移動
/// </summary>
/// <param name="aScrollBar">HScrollBarコントロール</param>
/// <param name="aDelta">マウスホイールの回転数</param>
/// <remarks>有効範囲(Minimum～Maximum)を超えないようガードを行う</remarks>
public static void HScrollBar_MouseWheel(HScrollBar aScrollBar, Int32 aDelta)
{
	Int32 newValue;
	
	newValue = aScrollBar.Value + (aDelta * SystemInformation.MouseWheelScrollLines / 120);

	// 有効範囲(Minimum～Maximum)を超えないようガード
	// (LargeChange - 1)はスクロールバーのThumbの幅を考慮したもの
	if (aScrollBar.Minimum <= newValue && newValue <= aScrollBar.Maximum - (aScrollBar.LargeChange - 1))
	{
		aScrollBar.Value = newValue;
	}
	else if (newValue < aScrollBar.Minimum)
	{
		aScrollBar.Value = aScrollBar.Minimum;
	}
	else if (aScrollBar.Maximum - (aScrollBar.LargeChange - 1) < newValue)
	{
		aScrollBar.Value = aScrollBar.Maximum - (aScrollBar.LargeChange - 1);
	}
	else
	{
		// DO NOTHING
	}
}
{% endhighlight %}