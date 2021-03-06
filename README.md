This is a learning project accessing Slack in a Windows / Windows Phone App

# TODO #

Strike through = Done

## Getting Setup ##
+ ~~Create Git Repo on TFS for shared work~~
	+ ~~Check in TODO from here~~
+ ~~Add Empty Project~~
+ ~~Add Empty Test Project~~
+ ~~Add Shared Items project for easier unit testing of non-ui code~~
+ ~~Spend time understanding the auth / calling API~~
	+ ~~CURL it up yo'~~
	+ ~~Check support for 'stuff didn't change since last request'~~ _(No, no caching)_
+ ~~Setup Fiddler, install certs~~

## Basic Data Access ##
+ ~~Add network request that outputs to the main content area on success and failure~~
+ ~~Add sample response file to repo~~
	+ ~~Normal response~~
	+ ~~Error responses detailed on api page~~
	+ ~~Mutated responses~~
+ ~~Add unit tests for parsing & handling the basic response~~
+ ~~Add support to writing the network response to disk~~
	+ ~~Probably should handle URL impact on network cache file~~ _Ignoring for now_
+ ~~Add loading data from disk if present & offline (go to network if online)~~
	+ ~~Refactor loading to skip real network requests when using testing~~
	+ ~~Mock offline network status check?~~ _Didn't need this due to the next item_
	+ _Yep!_ ~~Should be checking more for failure, rather than being online?~~
+ ~~Add Object model representing the items~~
	+ ~~Handle auth-level errors~~
	+ ~~Deserialize in some form from the JSON to the Object models~~
+ ~~Add support for merging any changes in a network request to offer change notification (Data already written to disk, so no need to write "diffs").~~
+ ~~Should this be done via an ID broadcast that is "no, you should probably load this item directly again"~~
	+ _Yes_ ~~Is this just making the thing too damn complicated?~~
+ Handle returning online when had started offline?

## UI ##
+ ~~Add listview, displays basic data through {binding}~~
+ ~~Create a user control for the list item~~
+ ~~Update listview to use CCC + add call back into custom control~~
+ ~~Add invoke handler to navigate to a new user detail page~~
+ ~~Add back requested support to navigate back~~
+ ~~Add new basic layout for user details on the new page~~
+ ~~Understand image size urls~~
	+ ~~Add to both list item~~, and details page
+ Add loading spinner to startup if > 150ms of load time
+ ~~Add support for splitting the view in full screen mode~~
	+ ~~Secondary frame, or primary frame that overlays the listview?~~
	+ Handle back button between the two worlds
	+ ~~Handle Resizing while navigated to an item~~
		+ ~~E.g. if on an item & small, when resized larger should show that item~~
		+ ~~if on an item when large, should navigate to that page when made smaller~~
		+ ~~Need to factor a view model now for the main page to keep state~~
+ ~~Use page/Control for user page as detail for master-detail~~
+ ~~Make layout look nice following 4px grid~~
+ Image loading seems inconsistent, and not as smooth as I'd like in the listview
	+ ~~Some images getting lost~~
	+ ~~Download images first to local disk for available offline~~
	+ no nice transitions when loading over the network
	+ Custom Image loading control to provide nice transition from blank to full?

## Possible Improvements ##
+ Use SQLite from Windows 1511 SDK for SQL Lite to store individual records & data
	+ Allows faster start up
	+ Creates case where only the IDs + viewport's data items are loaded
		+ Using Skinny + hydrate model
	+ Data probably isn't large enough right now to justify doing
		+ Might be fun though! :)

#### Reference ####
API Doc: https://api.slack.com/methods/users.list

You'll need an API token, which you can find details on here:
https://api.slack.com/authentication/basics