
###Learning Python 5th edition [nov2013-]
   - ebook
#####Chapter1-4
- basic intro, running scripts, exec, open, reload
- basic data types
- immutability (strings, numbers, tuples)
- help, dir functions
- raw strings r'C:\text\', bytes b''
- lists and list comprehension
- tuples immutable (see as read-only)
#####Chapter 5
- floor division //
- '{} or {0} string'.format()
- random.random, random.randint(a, b), random.choice(['a', 'b', 'c']), random.shuffle)
- Decimal, Fraction (limit_denominator)
- int('0xbo0-f', base_2_8_16) to convert string to int in a specific base
- Sets {1, 2, 3}
- must be explicitly created
- can contain only immutable/hashable elements
- frozensets can contain any type of object
#####Chapter 6
- types live with objects not variables
- everything is garbage collected using reference counting, at the point when there are no references
- as variables might point to the same object, changing the object in-place (only for mutable objects), might affect more variables **always use X.copy()**
  - use copy or deepcopy from the copy module to achieve this
- testing for same object *A is B*, also one can use sys.getrefcount(A) to see references to this object
#####Chapter 7 - Strings
- encode decode format() r'rawstrings' b'bytestrings' u'unicode\u022'
- triple quotes or block strings used for comments or multi-line strings
- we can test for string_a in string_b
- string formatting % always makes a new string when printing
  - print("string is %(named)d" % {'named': 'long'})
  - '{motto}, {0} and {food}'.format(42, motto=3.14, food=[1, 2])
  - '{}, {} and {}'.format('a', 'b', 'c')
  - 'My %(kind)s runs %(platform)s' % dict(kind='laptop', platform=sys.platform)
- int() chr() ord() for int/char/string conversion
#####Chapter 8 - Lists and dictionaries
 - lists: mutable, sub-nesting, accessed by offset, heterogeneous
 - list comprehension [c*2 for c in 'MONKEY']
 	- map does a similar thing, applying a function to a list(map(abs, [-1, -2, 1, 2, 3]))
 - slice assignment a_list[0:2] = ['one', 'two']
 	- [1, 2, 'spam'].sort() fails in python3 but works in 2.x
 - extends adds many elements, append only one
 - del(x[element]) deletes one or more elements
 - dictionaries: accessed by key, mutable, heterogenous, variable length
    - for key in Dict | (key, value) in Dict.items()
    - any immutable (object) can be a key in a dictionary
    - dict(zip(keys, values)) to quickly create a dictionary
    - has_key is deprecated in python3, use _**in**_ instead
    - dictionary comprehension {k: v for (k,v) in zip([1,2], ['a', 'b'])} or  Dict = {k: None for k in 'spam'}
    - items, keys and values() are now views and not elements
 - _can be sorted using **sorted(Iterable)**, which works for more any iterable_
#####Chapter 9 - tuples, files, ...
- tuple: ordered collections of elements, immutable, accessed by offset, can be seen as arrays of object references
    - the objects contained in tuples can be changed
    - namedtuples in collections module:
    	- Object = namedtuple('Name', ['structure', 'field'])
    	- instance = Object('Bob', 11.23)
- Files are buffered, we need to call flush or close to make sure everything is persisted
	- in python3 there's a clearer distinction between binary and text (including unicode) files
	- pickle is sort of a serialization basic function
	- there is also a **struct** module for handling C like structs
	- in pyhon2 there is also file() as well as open(), in py3 only open remained
- elements inside objects can be referneced by other objects so we need to be careful to work with copies if we need not to alter the originals, use slicing copy()/deepcopy() or create new objects
- we should not check for type(object) as it limits functionality
#####Chapter 10-13
 - intro to indentation and some pythonic rules :)
 - try: except: clause
 - **print([object, ...][, sep=' '][, end='\n'][, file=sys.stdout][, flush=False])** for python3
 - stream redirection (stdout, stderr), easiest is through assignment sys.stdout = open('file', 'w')
 - ellipsis can be used instead of pass **def to_be_implemented(): ...**
     - valid only in python3
 - 2 or 3, 3 or 2, 2 and 3, 2 and []
 - ternary expression Z = A if Condition else B
 - while conditions: (...) else: (...) _# if no break was encountered_
 - for _target_ in _object_: (...) else: (...) _# if no break was encountered_
 - zip() or map(); keys = [], values = [] => **`D = dict(zip(keys, values))`**
 - for (off, item) in enumerate('iterable'): ...
#####Chapter 14-17 - Iterators, Scope, ...
- iterator, any object which exposes \_\_next\_\_() and raises StopIteration at end of results
	- iterator object (\_\_next\_\_) or iterable object(\_\_iter\_\_)
	- files have their own iterators
- f = open(...), next(f) - will actually call f.\_\_next\_\_()
- list comprehensions might run faster because they run using compiled C code, this is especially true for large sets
- lines = [line.rstrip() for line in open('script.py')]
	- len([line for line in open(fname) if line.strip() != ''])  show # of lines
- similar to nested for loops: [x + y for x in 'abc' for y in 'lmn']
- map itself is also an iterable, applying a function call to a list list(map(str.upper, open('script2.py')))
- sorted() returns a list, not an iterable
- \*arg can be used to unpack values
- keys, values, items, range, map, filter, zip return iterable
- triple quoted strings can be accessed w/ \_\_doc\_\_, also existing modules documentation, i.e. sys.\_\_doc\_\_
- help(function/object/module) also gives valuable information
- online help can be served using the built-in server python -m pydoc
- Scope: LEGB rule - local (import builtins), enclosing (comprehension), global, built-in
    - namespace declarations: global, nonlocal; ie X = 1; def ...: global X, X=2
- factory functions / closures ; lambda's
- nonlocal - a name that can be changed in an enclosing scope
#####Chapter 18 - Arguments
- positional arguments matched from left to right
- keywords matched using the parameters names
- use \* or \*\* varargs to match any number of parameters as tuples (positional) or dictionaries (keyword)
- if we have the following def f(a, \*pargs, \*\*kargs): print(a, pargs, kargs)
- then calling f(1, 2, 3, x=1, y=2) will result in  1 (2, 3) {'y': 2, 'x': 1}
- similarly `def kwonly(a, *, b, c='spam'): print(a, b, c)` will work for kwonly(1, b='eggs') => 1 eggs spam but not for _kwonly(1, c='eggs')_ => TypeError: kwonly() missing 1 required keyword-only argument: 'b'
- sys.getrecursionlimit() to get/set higher limits for stack
- functions can have annotations in Python3
- anonymous functions (lambdas): no ifs are allowed, local scope for variables
    - remember the scoped LEGB rule, the same applies for lambdas
    - f = lambda x, y, z: x + y + z
- functional programming: map, filter, reduce
    - apply function to an iterable - map - map(my_function, list)
    - i.e. list(map(pow, [10,10,10], [2,3,4]))
    - selecting items in iterables - filtering - list(filter((lambda x: x>0), [3, 5, -1, 9, -9, -100]))
    - reduce - returning an element after scanning an iterable: reduce((lambda x, y: x * y), [1, 2, 3, 4]) => 24
- list comprehension collect the result of applying an expression to an iterable, and return a list i.e. `res = [ord(x) for x in 'spam']
  - sometimes map or list comprehension are better suited for the task-at-hand, for simple scenarios, you can get either of them quite straightforward
  - as in Python3 file is iterable [line.rstrip() for line in open('file')] == list(map(lambda line: line.rstrip(), open('file')))
- the _timeit_ module used for time length statistics of function calls, pystones
#####Chapter 22-25 - Modules/Packages/Advanced Modules
- modules are imported only once per session, so in interactive mode you need to use `reload` instead of just calling import again
- we can use .pth files to define other paths where Python can search for modules
- prefer `import` over `from`, when working with modules but no strong preference is given to import
- `import as` can be used in order to rename modules or to avoid name conflicts
- namespace nesting works down (mod1 imports mod2 which imports module3) but not upwards, so module3 can't access mod2 or mod1
- reload is imp.reload in Python3; a module must be imported first, before we can reload it
    - using from is not affected by reloads, so we must use import if we want to use reload
- each module folder must contain an `__init__.py` file and the code within this file is executed automatically on import
    - \_\_all\_\_ lists inside the files define what modules are imported on `from *` statements
    - `from A import b` will make it easier in the future if refactoring is needed where as import is a bit more cumbersome to update
    - `import A as B` addresses this issue and also makes it easier for future adjustments
- we will need to use _import_ and not _from_ only if we want to use the same property across modules and then we will need to specify the full path to the object
    - relative imports, specific to Python 3.x only apply to from imports and only to the interpackage imports starting with . or ..
    - in Python 3.x from A import B are always absolute imports
- types of imports for Python 3.3+
    - basic module imports: import MOD, from MOD import ATTR
    - package imports: import dir1.dir2.MOD, from dir1.MOD import ATTR
    - package relative imports: from . import MOD (relative), import MOD (absolute)
    - namespace packages: import splitdir.MOD
- we can hide some of the names for `from` by using either \_\_all\_\_ or _Underscore for declarations
- future imports backported to previous versions can make use of the \_\_future\_\_ feature
- use \_\_name\_\_ to be able to import or use as a module a certain file
    - we could also use this feature for (unit) testing the module


###Boneshaker by Christie Priest [aug2012-oct2012]
In an approximate version of the Seattle gold rush, a true steampunk story
involving a deadly gas, drugs, leather and a cloudy and misty atmosphere.
Did I mention zombies? Or airships powered by steam?
Overall a nice and short read with a good story. Rating 4/5

###Don't Make Me Think by Steve Krug [oct2012]
The "bible" of web usability in its second incarnation. A couple of ideas or reminders from the book:

+ Make the site natural to the user and his actions
+ Build billboards not newspapers
+ Make stuff visible and easy to determine what's its function to the user
+ "Get rid of half the words on each page, then get rid of what's left"
+ Home page is really an important starting point in the design, although everybody wants to have its saying about it.
+ make clear what's the mission of the site, easily done through displaying a tagline (5-8 words)
+ make sure the home page conveys just the main objective of the site and not an in-depth review of what the site does
+ have a clear separation of the main tagline, categories, description, search and others
+ usability: testing earlier is better and cheaper than doing it at the very end of the project
+ to get a new perspective on the site you're building, you must test it
+ testing some parts by even 1 user is better than no testing at all
+ focus groups help establishing the target user group of the site before the design phase starts
+ try to involve different people from different teams in order to get more traction and involvement during the (usability) testing
+ ask the tester to do some specific tasks besides
+ After the walkthroughs review/go over the notes as soon as possible

###The Lean Startup by [jan2013-may2013]
+ Going after a couple of ideas of what make a startup tick, and how can you avoid falling in the most common pitfals of the startup movement.
+ Talking about `validated learning' where all the steps you take are directed by input coming from the customers and not from the bussiness owners. A couple of examples presented like the IMVU service, the laundry in India, or Kodak photo share which all started with a basic product, and improving that by getting input from customers instead of having a plan before going to market.
- MVP description and what’s it about. Always strive to keep the feature creep to a minimum and deliver to the early adopters, whom are people to prefer somewhat incomplete products just to gain the incentive of being first users - which might be an advantage to them or their company  by being first barch of users.
- The leap-of-faith assumption refers to one thing that the startup assumes to be correct withou prior validation, but in which the MVP helps to make a sale.
The Dropbox example where a “how does it work” video became the MVP that went through the features - sync made easy - but at the same time the leap-of-faith was the assumption that similar products where too difficult to use.
- Food on the table story - “concierge” approach - one customer initially interacted directly with the founder in order to get an insight in building the product.
- Use the so called ""Innovation accounting" for the startup as an accounting method

##Understanding Search Engines
Last 2chapters skim over HCI regarding the search engine “visible to the user part”. Last chapter has an index with all important references to articles/books presented throughout the book and can be an useful goto index.

##Drawing on the right side of the brain[2013-]
The author goes over some (non scientifically) proven concepts that one brain hemisphere is dedicated to different things LEFT for science and the RIGHT for arts. And as an intro makes you do your portrait.
