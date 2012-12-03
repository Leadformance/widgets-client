Store Locator plugin
====================

Version History
--------------------------------------

### 1.3 ###
- Added an option to filter search result
- Added an option to display opening hours and time before to close
- Added an option to display customized content 
- Added an option to call automatically the widget
- Use pos type parameter to not display the link on pos title if there is no pos page
- Fix geolocation on IE7/8/9 and Firefox 3.0

### 1.2 ###
Added a compatible JS file for jQuery < 1.5 versions

### 1.1 ###
- api_uri is now customizable
- Changed a variable from 'language' to 'lang' which was the reason why IE crashed 
- Changed the alert to window.console for logging purpose
- Added a a link around the span of the pos title

Plugin setup
--------------------------------------

To use the store Locator plugin you'll need ( _these lines are already provided in index.html in the package_ ): 

1. jQuery >= 1.7.1 ( http://code.jquery.com/jquery-1.7.2.min.js )
2. Include Google Map V3 API ( http://maps.google.com/maps/api/js?sensor=false )
3. Include Store Locator plugin ( http://widgets.leadformance.com/storeLocator/v1/lf_storelocator.min.js )
4. Call the plugin ( _default values_ ):

				<script type="text/javascript">  
					$(function(){  
						$('.lf_storeLocatorWidget').lf_storelocator({  
							api_key: "myapikey", 
							api_uri: "myapiURL",
							fo_uri: "myfoURL",
							allow_geolocation: true,
							lang: "fr"
						});  
					});  
				</script>

4. Automatic call of the plugin :

				<script type="text/javascript">  
					$('.lf_storeLocatorWidget').lf_storelocator({  
						api_key: "myapikey", 
						api_uri: "myapiURL",
						fo_uri: "myfoURL",
						allow_geolocation: true,
						lang: "fr"
					});  
					$('.lf_storeLocatorWidget').lf_storelocator.launch_lf_storelocator('','',false,true,'',45.8992470,6.1293840,true);	
				</script>
				
To understand how to set your widget, please find examples from http://widgets.leadformance.com/storeLocator/examples/index.html

Plugin options
--------------------------------------

You can customize your plugin with the following options : 

### api_key ###
**Mandatory.**
Type : String  
Leadformance API Key

### max_results ###
Type : Integer  
Default : 3  

### fo_uri ###
Type : String  
Your Front office URL. If missing, some fonctionnality will be disabled.  

### allow_geolocation ###
Type : boolean  
Default : true  
Allow your visitor to use geolocation fonctionnality (only available for compatible browsers : IE9+, FF3.5+, Chrome 5+, Safari 5+, Opera 10.60+)  

### lang ###
Type : String  
Default : "en"
Available : "fr", "de", "nl"
If the language asked isn't found, it'll display english texts.  

### lang_override ###
Type : Object  
Override the default language and the "lang" parameter.   

**Available parameter :**

* formLabelFind
* formPlaceHolder
* formLabelGeoloc
* errorNoData
* errorNoResult
* errorGeoLoc
* errorTryAgain
* errorXHR
* textVisitUs
* hours_start
* hours_end
* hours_closed
* hours_day_label
* hours_eoh_label
* hours_eoh_opened
* hours_eoh_closed
* hours_eoh_start
* hours_eoh_end
* hours_eoh_and
* hours_eoh_month
* hours_tbtc_closed
* hours_tbtc_eoh_closed
* hours_tbtc_eoh_opened
* hours_tbtc_opened
* hours_tbtc_hour
* formLabelGeolocIE8
		
**Example :**

				$(function(){  
					$('.lf_storeLocatorWidget_submit').lf_storelocator({  
						lang: "fr",  
						lang_override:  
						{  
							'formLabelFind': 'Find a store near Paris',  
							'textVisitUs': 'Klicken Sie auf Besuch'  
						}  
					});  
				});`  

### filter_values ###
Type : String  
Default : ""
Contains the list of values used by the filter. The goal is to filter the search result.
If there is multiple values, you have to separate them with the couple of characters "##"

### filter_name ###
Type : String  
Default : ""
Name of the field used to filter the search result. If the name is not "id","custom_id" or "service_inventory_id", it's a smart tag
!!WARNING!! : In case of smart tag, the widget do a call for each pos in the search result. Thus, your credit will be decremented for each call.

### filter_hide ###
Type : Boolean  
Default : false
If the value is "true", all pos whose the value is in "filter_values" are hided, else all pos whose the value is in "filter_values" are displayed

### filter_all ###
Type : Boolean  
Default : false
Used to display all poses from a filter or to add the class "inactif"

### custom_values ###
Type : Boolean  
Default : false
Used to dislay common content to each pos in the search result or to display specific content to each pos in relation with "filter_values"

### position_latitude ###
Type : Float  
Default : 0
Used with position_longitude to obtain list of poses for geolocation

### position_longitude ###
Type : Float  
Default : 0
Used with position_latitude to obtain list of poses for geolocation

### display_hours ###
Type : Boolean  
Default : false
Used to display standard and exceptional opening hours. Used to display time before to close.

### extra_search ###
Type : String  
Default : ""
Allow to apply a smart tag filter directly on the search. 
This filter is different than "filter_values" because with "filter_values" the filter is applied after the search. 
With this parameter, the filter is applied during the search.   

CSS customization
--------------------------------------

You can fully customize the HTML with the CSS joined to your package. Take care not to delete the class needed by the plugin : 

* **.lf_storeLocatorWidget** for your main container
* **.lf_storeLocatorWidget_find** for your search field
* **.lf_storeLocatorWidget_submit** for the search button
* **.lf_storeLocatorWidget .lf_openinghoursdays** for opening hours
* **.lf_storeLocatorWidget .lf_distantexceptionalopeninghours** for exceptional opening hours

