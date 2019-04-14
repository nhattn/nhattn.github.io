---
layout: post
title: React Native Show Progress bar While Loading WebView Android iOS
comments: false
category: React Native
tags: react native
---

This tutorial is the second part of our Previous React Native [Simple WebView Tutorial](https://reactnativecode.com/embed-load-http-url-webview-example/). In this tutorial we would going to create a react native application with WebView component and Show Progress bar – ActivityIndicator on middle of screen just above WebView on Website loading time and hide the Progress bar after done loading WebView and show Website using `renderLoading={}` and `startInLoadingState={}` method.

### Contents in this project Show Progress bar While Loading WebView in Android iOS Example Tutorial :

1. Import `StyleSheet`, `WebView`, `Platform` and `ActivityIndicator` component in your react native project.

{% highlight js %}
import React, { Component } from 'react';

import { StyleSheet, WebView, Platform, ActivityIndicator} from 'react-native';
{% endhighlight %}

2. Create a function named as `ActivityIndicatorLoadingView()` . Inside this function we would make a ActivityIndicator component View in return block. This function would render the ActivityIndicator just middle of screen above WebView.

{% highlight js %}
ActivityIndicatorLoadingView() {
	return (
		<ActivityIndicator
    		color='#009688'
    		size='large'
    		style={styles.ActivityIndicatorStyle}
  		/>
	);
}
{% endhighlight %}

3. Create *WebView* component inside render’s return block.

*renderLoading* : Call the ActivityIndicatorLoadingView function which would render the ActivityIndicator .

*startInLoadingState* : This would allow us to start the render loading view.

{% highlight js %}
render() {       
	return (
		<WebView 
			style={styles.WebViewStyle} 
			source={{uri: 'https://google.com'}} 
			javaScriptEnabled={true}
			domStorageEnabled={true}
			renderLoading={this.ActivityIndicatorLoadingView} 
			startInLoadingState={true}  
		/>
	);
}
{% endhighlight %}

4. Create Custom CSS Style Class for WebView and ActivityIndicator.

{% highlight js %}
const styles = StyleSheet.create({
	WebViewStyle: {
   		justifyContent: 'center',
   		alignItems: 'center',
   		flex:1,
   		marginTop: (Platform.OS) === 'ios' ? 20 : 0
	},
	ActivityIndicatorStyle:{
    	position: 'absolute',
	    left: 0,
	    right: 0,
	    top: 0,
	    bottom: 0,
	    alignItems: 'center',
	    justifyContent: 'center'
	}
});
{% endhighlight %}

### 5. Complete source code for `App.js` File :

{% highlight js %}
import React, { Component } from 'react';
import { StyleSheet, WebView, Platform, ActivityIndicator} from 'react-native';
export default class MainActivity extends Component {
	ActivityIndicatorLoadingView() {
    	return (
		    <ActivityIndicator
        		color='#009688'
        		size='large'
        		style={styles.ActivityIndicatorStyle}
      		/>
    	);
  	}
    render() {      
       	return (
            <WebView 
    		    style={styles.WebViewStyle} 
         		source={{uri: 'https://google.com'}} 
         		javaScriptEnabled={true}
         		domStorageEnabled={true}
         		renderLoading={this.ActivityIndicatorLoadingView} 
         		startInLoadingState={true}  
         	/>
        );
    }
}
const styles = StyleSheet.create({
	WebViewStyle:{
		justifyContent: 'center',
		alignItems: 'center',
		flex:1,
		marginTop: (Platform.OS) === 'ios' ? 20 : 0
	},

	ActivityIndicatorStyle:{
		position: 'absolute',
		left: 0,
		right: 0,
		top: 0,
		bottom: 0,
		alignItems: 'center',
		justifyContent: 'center'
	}
});
{% endhighlight %}

*Screenshot in Android device :*

![Android 01](/public/uploads/2019/04/Progressbar_WebView_1_Android.png)

![Android 02](/public/uploads/2019/04/Progressbar_WebView_2_Android.png)

![iOS 01](/public/uploads/2019/04/Progressbar_WebView_1_iOS.png)

![iOS 02](/public/uploads/2019/04/Progressbar_WebView_2_iOS.png)