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
#####Chapter 10/11
 - intro to indentation and some pythonic rules :)
 - try: except: clause
 - **print([object, ...][, sep=' '][, end='\n'][, file=sys.stdout][, flush=False])** for python3
 - a
	
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
