# Clojure Notes

## Use, Import, Require

- **require** brings one or more quoted symbols or vectors of quoted symbols into the current namespace for use with fully qualified name.  If `as` option is used you can alias the longer namespace. `refer` option allows you to selectively choose which functions in the namespace to export.
- **use** no longer required as `require` takes the refer option which essentially does the same thing.
- **import** how you get at java code.


## Clojure: Methods to Remember


Use compose more!!!!!

- **alter** - used to read and update a ref
- **apply** - `([f args] [f x args] [f x y args] [f x y z args] [f a b c d & args])`
- **aset** - set the value in java array.
- **assoc** - returns a new collection with the value at index / key updated.
- **butlast**
- **commute** - similar to alter but STM can reorder commutes.
- **comp** --  take a set of functions and return a function that is the composition of those functions
- **comp** - Like thread first but not … research this
- **compare** - returns -1 0 1 when comparing 2 data structures
- **complement** - reverses truthy function.
- **concat**
- **conj** - Is different for list and vector, end of vector, front of list
- **contains?** - Tests a a map for the presence of a key regardless if its value is nil.
- **deref (@)** - Get the value of a mutable thing.
- **destructuring** - you know what this is.
- **diff** - Recursively compares two data structures
- **dissoc** - Returns a map with a key removed
- **do** - Do 1 or several imperative things.  Useful when some other form only executes 1 form in a branch such as in (if)
- **doseq** - iterate over a seq e.g something with a first and reset.  For x in xs do something side-effecty.
- **dosync** - Perform expressions within a transaction.
- **drop** - Drops x amount of items from collection
- **drop-while** - Drop from a sequence while a predicate is true.
- **every?**
- **false?**
- **filter** - filters a collection by a predicate that returns true or false for each element.
- **find-doc** - searches function names AND doc strings
- **first**
- **for** - comprehension for things without side-effects
- **frequencies**
- **get** - looks up a keyed value in a collection
- **get-in** - returns a value from a nested associative structure.
- **group-by**
- **hash-set** - Creates a set from multiple arguments
- **identical?** - true when symbols are the same object
- **identity**
- **interleave**
- **interpose** - like join but not with strings… returns a seq of elements separated by
- **into-array** - makes a java / javascript array out of a vector
- **iterate** - Returns a lazy sequence of x, (f x), (f (f x)) etc. f must be free of side-effects
- **keep**
- **Keys**
- **last**
- **list**
- **map** - `([f coll] [f c1 c2] [f c1 c2 c3] [f c1 c2 c3 & colls])`:
  It is worth noting that when a single collection is given, map iterates over it while when
  multiple collections are given, it iterates over each collection executing on the first element of each collection, then the second argument of each collection, etc.
  	
  		Ex: (map list [1 2 3] [4 5 6]) ((1 4) (2 5) (3 6))
- **mapcat**
- **merge** - Combines maps.  If multiple maps contain a key.  Rightmost wins.
- **merge-with** - merges two maps.  Uses a function to specify merge rule.
- **next**
- **not-every?**
- **nth**
- **partition**
- **partition-all** - returns a lazy sequence of lists but may include partitions with fewer than n items at the end.
- **partition-by**
- **partial** - Build a function from the partial application of another function.
- **peek**
- **pop** - returns rest of list, vector minus last element
- **quote**
- **range**
- **rationalize** - converts number to rational
- **rational?**
- **ratio?**
- **reduce** - like inject in ruby
- **ref-set** - sets the value of a ref
- **rem** - remainder
- **remove** - returns a lazy sequence of the items in a coll for which pred returns false.l
- **repeatedly**
- **re-find** - like ruby match
- **reset** - Sets the value of an atom without regard for the previous value.
- **re-seq** - returns a lazy seq of all matches.
- **reset!** - Set the value of an atom.
- **rseq** - Returns a reversed seq on a collection
- **repeat**
- **rest**
- **reverse**
- **set** - Creates a set out of a collection (such as a sequence)
- **select-key** - intersection of keys
- **select-keys** - returns a map keeping only the keys passed in.
- **send** - Function application for updating an agent.  Used when update action will not block.
- **send-off** - Function application for updating an agent.  Used when the update action will block like writing to a file.  It will get its own thread pool.
- **sep**
- **seq** - Returns a seq on a collection
- **some**
- **sort-by**
- **split-at** - Splits a sequence at an index
- **split-with** - Takes a predicate and splits the sequence into two collections.  Ones that satisfy the predicate and those that don't
- **subvec** - Returns a sub vector of a vector
- **swap!** Function application on an atom for updating.
- **take-while** - Take from a sequence while a predicate is true.
- **true?**
- **vals**
- **vector** - Creates a vector from multiple arguments
- **vec** - Creates a vector from a collection (such as a sequence)
- **when-not** - like unless


## Vectors:
- **into** - "pour" values into a vector.
- **vector** - builds a vector from its arguments
- **vec** - casts a seq to a vector
- **assoc** - change item in a vector
- **subvec** - like splice


Vector like a stack: conj (push) and pop
- **peek** looks at last item added to stack that would be popped off

Vectors and Seqs:
- **replace** - uses the most efficient way per data structure.

Vectors and Maps:
Working with nested structures
- **assoc-in** - Replaces a value in nested structure (Matrix)
- **get-in** - Gets value in nested structure (Matrix)
- **update-in** - takes a function to APPLY to an existing value in a nested structure

Vectors are efficient at three things compared to lists:
 1. Adding or removing things from the end of the collection.
 2. Accessing or changing items in the interior of the collection by numeric index.
 3. Walking in reverse order.

## Lists

- The correct way to add to a list is with conj
- conj will add to the left side of the list


(.printStackTrace *e) - After an error in the repo, print stack trace


Learn seq function 


Forms to remember:
if
and
->
->>


-> or ->>
 - Allows you to read left to right instead of right to left due to nested function calls
 - Useful for deeply nested data structures

-> adds arg to front of first form
->> ads arg to end of first form



clojure.core and clojure.data are your friends
• Break apart the problem to identify pure functions.
• Learn the standard library so you can find functions already written. • Pour no concrete (use data as data).
• Test inside out from the REPL.

The branch of math that deals with the different ways of forming patterns is called enumerative combinatorics.

## Maps:
- Are functions of their keys

        ({:first "foo" :second "bar"} :first)
        ; "foo"
         
## Keywords
- Are functions.  They take collections as their argument and look themselves up

        (:first {:first "foo" :second "bar"})
        ; "foo"

## Sets:
- Sets act as functions
- \#{}

## Set Theory:
- The union of {1, 2, 3} and {2, 3, 4} is the set {1, 2, 3, 4}
- The intersection of {1, 2, 3} and {2, 3, 4} is the set {2, 3}
- {1,2,3} and {2,3,4} , the symmetric difference set is {1,4}
- The set difference {1,2,3} \ {2,3,4} is {1} , while, conversely, the set difference {2,3,4} \ {1,2,3} is {4}
- The cartesian product of {1, 2} and {red, white} is {(1, red), (1, white), (2, red), (2, white)}.
- For example, the power set of {1, 2} is { {}, {1}, {2}, {1,2} }
- Some basic sets of central importance are the empty set (the unique set containing no elements), the set of natural numbers, and the set of real numbers.


functions act differently depending on what data structure they are performed on.

## Sequences

ALL persistent collections use closures sequence abstraction!

A persistent collection in Clojure allows you to preserve historical versions of its state and promises that all versions will have the same update and lookup complexity guarantees.

A sequential collection is one that holds a series of values without reordering them.

A sequence is a sequential collection that represents a series of values that may or may not exist yet.  They may be values from a concrete collection or values that are computed as necessary.  A sequence may also be empty.

seq is Clojures api for navigating collections.  It consists of two functions: first and rest. A seq is any object that implements the seq API, thereby supporting the functions first and rest.  Like an immutable variant of enumerator or iterator.

### *Aside* When would you use vector, hash-set, set, vec, list, etc?

When generating sequences (like a range of numbers) you would then pass that sequence to one of the previous functions to create a specific type of collection out of it as a sequence doesn't have a particular collection type.


## Big-O notation: Notation for describing the complexity of an algorithm .

Finding an element in a linked list is O(n) which is read order n.

Finding :a in list (:a :b :c) is O(1) which is read as constant time.
O(n) is also known as linear time.

Constant term: work that the algorithm has to do up front regardless of the size of the work load.



## Macros:
- ' or (quote) prevents list from being evaluated
- Syntax quote `
- unquote ~
- unquote-splice ~@
- capture symbolic name within body of macro ~’
- Macros almost always return a list
- Macro arguments can be destructured just like functions
- Unlike functions, macro arguments are not evaluated before passing into the function
- Macros can be multi arity
- You'll almost always use quoting within your macros so that you can obtain an unevaluated symbol
- Don't need to quote passed in expression because those won't be evaluated until expansion
- Do need to quote forms that shouldn't be evaluated until expansion.    We want these added to the list that will then be eval'd. This allows us to use forms / functions within the function to do manipulations.
- Use do to wrap up many forms to be evaluated
- Helper functions may be used to DRY out macros and add more complexity but these functions
should adhere to the same quoting practices.
		
Example:

		(defmacro code-critic
  			"phrases are courtesy Hermes Conrad from Futurama"
  			[{:keys [good bad]}]
  			(list 'do
       			 (list 'println
            			  "Great squid of Madrid, this is bad code:"
            			  (list 'quote bad))
       			 (list 'println
             			 "Sweet gorilla of Manila, this is good code:"
            			  (list 'quote good))))

			(code-critic {:good (+ 1 1) :bad (1 + 1)})
			; =>
			Great squid of Madrid, this is bad code: (1 + 1)
			Sweet gorilla of Manila, this is good code: (+ 1 1)
			
### Syntax Quoting

Syntax quoting can return unevaluated data structure similarly to quoting. There's one important difference, though: syntax quoting will return the fully qualified symbols so that the symbol includes its namespace.  This helps prevent name collisions.

The other difference between quoting and syntax-quoting is that the latter allows you to unquote forms with the tilde, ~. Unquoting a form evaluates it.

Syntax quoting basically allows you to reverse the default way macros are evaluated.

	;; Quoting does not include a namespace unless your code includes a namespace
	'+
	; => +
	
	;; Write out the namespace and it'll be returned
	'clojure.core/+
	; => clojure.core/+
	
	;; Syntax quoting will always include the symbol's full namespace
	`+
	; => clojure.core/+
	
	;; Quoting a list
	'(+ 1 2)
	; => (+ 1 2)
	
	;; Syntax-quoting a list
	`(+ 1 2)
	; => (clojure.core/+ 1 2)
	
	;; The tilde (~) unquotes the form "(inc 1)"
	`(+ 1 ~(inc 1))
	; => (clojure.core/+ 1 2)
	
	;; Without the unquote, syntax quote returns the unevaluated form with
	;; fully qualified symbols:
	`(+ 1 (inc 1))
	; => (clojure.core/+ 1 (clojure.core/inc 1))
	
The takeaway:

	;; Building a list with the list function
	(list '+ 1 (inc 1))
	; => (+ 1 2)
	
	;; Building a list from a quoted list - super awkward
	(concat '(+ 1) (list (inc 1)))
	
	;; Building a list with unquoting
	`(+ 1 ~(inc 1))
	; => (clojure.core/+ 1 2)
	
Without syntax-quote, we need to use the list function. Remember that we want to return a list which will then be evaluated, resulting in the quoted function being applied.  The list function isn't necessary when we use syntax-quote, however, because a syntax-quoted list evaluates to a list — not to a function call, special form call, or macro call.

Without syntax-quote, we need to quote the symbol of functions we don't want evaluated until expansion. This is because we want the resulting list to include the symbol of the function, not the function which the symbol evaluates to.

By comparison, symbols within a syntax-quoted list are not evaluated; a fully-qualified symbol is returned. A function that we don't want evaluated until expansion thus doesn't need to be preceded by a single quote.
			
Same Example, Syntax Quoted:

	(defmacro code-critic
	  "phrases are courtesy Hermes Conrad from Futurama"
	  [{:keys [good bad]}]
 	 `(do (println "Great squid of Madrid, this is bad code:"
 	               (quote ~bad))
  	     (println "Sweet gorilla of Manila, this is good code:"
  	              (quote ~good))))
			
Another Example:
			
		(defmacro unless
  			"Inverted 'if'"
  			[test & branches]
  			(conj (reverse branches) test 'if))

			(macroexpand '(unless (done-been slapped? me)
 			                     (slap me :silly)
 			                     (say "I reckon that'll learn me")))
			; =>
			(if (done-been slapped? me)
 			 (say "I reckon that'll learn me")
  			(slap me :silly))


## Software Transactional Memory:
A transaction in clojure is remarked by dosync and is used to build a set of changeable data cells embeded within that should all change together.  This is similar to a database transaction.



- Clojure provides four different reference types to aide in concurrent programming:
  - Refs, agents, atoms, and vars.
  - All but vars are considered shared references and allow changes to be made across threads of execution.
- Ref is Coordinated and Retriable
- Agent is Asynchronous
- Atom is Retriable
- Var is Thread-local

### Refs: Great for coordinated access to shared state
- Must be done within a transaction using `dosync`
- Coordinated: reads and writes to multiple refs can be made in a way that guarantees no race conditions.
- Asynchronous: the request to update is queued to happen in another thread some time later, while the thread that made the request continues immediately.
- Retriable: the work done to update a reference’s value is speculative and may have to be repeated.
- Thread-Local: Thread safety is achieved by isolating changes to state to a single thread.
- @ or deref are used to access values of a reference type.
- Use alter, ref-set, and commute to update the value within a ref


### Atoms: Great for uncoordinated updates
- Atoms are like refs in that they’re synchronous but like agents they are independent (uncoordinated).  They could be used to keep track of the currently playing track but if you wanted to update the current track and current composer in lock step you would use a ref. (you could also store track and composer as a map and then perform updates on that instead.)
- Use reset! to update an atom
- Use swap! to only update a part of an atom???


### Agents:
- Each agent has a queue of actions that need to be performed on its value and each action will product a new value for the agent to hold and pass to subsequent action.
- Update an agent using send or send-off.
- Use send-off if the action does I/o or may block otherwise use send.
- When agents fail they must be restarted.


### Vars:
- Can be named and interned in a namespace.
- Dynamic vars can provide thread-local state.


## Web Notes:

- Compojure
- Ring
- ring-middleware-json: Middleware to turn json body into params.
- Liberator: Turns routes into resources. Uses a decision graph to determine response.
- Cheshire: Parsing json
- clojure.data.json: Manipulate json data
- lib-noir
	- session, cookies, redirection, crypt (password hashing)
	- validation: Adds ability to validate params
- clojure.data.jdbc: Database connector
- korma: Database abstraction
- clj-pdf
- http-kit for websockets
- hiccup: Clojure html templating



## New Workflow New Namespace



