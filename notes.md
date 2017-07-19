* Store
	* React-Redux: The store comes from the default store paramter in the reducer or reducers
	* Elm: The store comes from the model definition and the init function
* Reducer
	* React-Redux: Function which takes in the store and an action and returns the store
	* Elm: Update function which takes in the store and a Msg, returning a tuple containing the store and a Cmd
* Producing Side Effects (communicating with the outside world or doing something non-reproducible)
	* React-Redux: Dispatch Thunk instead of action
	* Elm: Commands (AJAX, Random Numbers)
* Component
	* React-Redux:
		* Can be functional or React classes
		* The app must be connected to the store with the Provider component
		* Components must be connected to the store with 'connect()' to look at it or dispatch actions
	* Elm: Function which returns an Html Msg
		* Functional only
		* No JSX, must use functions imported from the Html library
		* The view function is given the model, so all components can see the model if they are passed it
		* The view function must produce a Html Msg, which stands for an Html object which can produce a Msg
		* When a Msg is produced, it automatically gets sent to the update function
		* Msg's are produced through the on* attributes of an HTML element, imported from Html.Events
* External Events (WebSockets)
	* React-Redux: Middleware to handle externally initiated events
	* Elm: Subscriptions which fire off a Msg with additional data
* Breaking up a complex app
	* React-Redux: use combineReducers to separate functionality by store key
	* Elm: Each section will have it's own custom Msg type (called something else) and it's own update function. These will be exported. In the main elm file, they are imported. The individual Msg types are unioned together into the master Msg type and given to the program. The master update function (given to the program) is made up of a case statement which routes the Msg into the individual update functions depending on the Msg subtype.
* JS-Interop
