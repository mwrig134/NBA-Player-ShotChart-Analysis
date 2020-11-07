We did a very simple translation from X and Y coordinates to latitude and longitude. 
Add new columns in Panda so the court is evenly displayed

After adding lat and lon, we then uploaded the data to CartoDB. Then it was time to display it in Leaflet.
Aiming to add interactive hovertools to portray every shot's statistic. 

	cartodb.createLayer(mapchart, {
	    id:"6eadec2c-0204-11e6-865f-0e674067d321",
	    user_name: 'latimes',
	    type: 'cartodb',
	    cartodb_logo: false,
	    sublayers: [{
	      sql: "SELECT * FROM kobe_all_shots_geocoded_final_merge ORDER BY priority,event_type DESC",
	      layer_name: "allshots",
	      cartocss: cssString,
	      interactivity: "combined_shot_type,action_type,season,event_type,shot_distance,playoffs,opponent,game_date",
	      attribution: "Source: stats.nba.com"
	    }]

	  });

    cartodb.createLayer is a method of cartodb.js that lets you quickly create a leaflet layer from a CartoDB dataset. It uses CartoCSS for styling. Here's an example of that:

	    }\
	      [event_type = 'Missed Shot']{\
	        marker-fill: #F5D05E;\
	        marker-line-width: 0.5;\
	        marker-fill-opacity: 0.5;\
	        marker-line-color: #cacaca;\
	        marker-line-opacity: 0.6\
	    }\
	    marker-allow-overlap: true;\
	     [zoom = 16] { \
	       marker-width: " + baseMarkerWidth * 24 +"; \
	     } \
	    [zoom = 15] { \
	       marker-width: " + baseMarkerWidth * 17 +"; \
	     } \
	    [zoom = 14] { \
	       marker-width: " + baseMarkerWidth * 10 +"; \
	     } \
	     [zoom = 13] { \
	       marker-width: " + baseMarkerWidth * 6 +"; \
	     } \
	     [zoom = 12] { \
	       marker-width: " + baseMarkerWidth * 4 + "; \
	     } \
	    [zoom = 11] { \
	       marker-width: " + baseMarkerWidth * 2 + "; \
	     } \
	    [zoom = 10] { \
	       marker-width: " + baseMarkerWidth + "; \
	     } \
	}";
  
  The newest addition for this would need to be so that a user can go through and see a "drop down" list without clicking, while just hovering their mouse.
