# ddd-reference

Definitions and Pattern Summaries -- Eric Evans

## Definitions

+ domain
    + A sphere of knowledge, influence, or activity.The subject area to which	the user	applies	a program	is	the	domain	of	the	software.
+ model
   + A	 system	 of	 abstractions	 that	 describes	 selected	 aspects	 of	 a domain	 and	 can	 be	 used	 to	solve	problems	related	to	that	domain
+ ubiquitous	language
   + A	 language	 structured	 around	 the	 domain	 model	 and	 used	 by	 all	 team	 members	 within	 a	bounded	context	to	connect	all	the	activities	of	the	team	with	the	software.
+ context
    + The	setting	in	which	a	word	or	statement	appears	 that	determines	its	meaning.	Statements	about	a	model	can	only	be	understood	in	a	context.	
+   bounded	context
    +   A	description	of	a	boundary	 (typically	a	subsystem,	or	the	work	of	a	particular	team)	within	which	a	particular	model	is	defined	and	applicable

Pattern	Language	Overview 见图

## I. Putting	the	Model	to	Work

Domain-Driven	Design	is	an	approach	to	the	development	of	complex	software	in	which	we:

1. Focus	on	the	core	domain.
2. Explore	 models in	 a	 creative	 collaboration	 of	 domain	 practitioners	and	software	practitioners.
3. Speak	a	ubiquitous	language within	an	explicitly	bounded	context.

### Bounded	Context

*Multiple	 models	 are	 in	 play	 on	 any	 large	 project.*

Model	expressions,	like	any	other	phrase,	only	have	meaning	in	context.

**Explicitly	 define	 the	 context	 within	 which	 a	 model	 applies.	 Explicitly	 set	 boundaries	 in	terms	 of	 team	 organization,	 usage	 within	 specific	 parts	 of	 the	 application,	 and	 physical	manifestations	such	as	code	bases	and	database	schemas.	Apply	Continuous	Integration	to	keep	 model	 concepts	 and	 terms	 strictly	 consistent	 within	 these	 bounds,	 but	 don’t	 be	distracted	or	confused	by	issues	outside.	Standardize	a	single	development	process	within	the	context,	which	need	not	be	used	elsewhere.**

### Ubiquitous	Language

Within	a	single	bounded	context,	language	can	be	fractured	in	ways	that	undermine	efforts	to	
apply	 sophisticated	 modeling.	 If	 the	 model	 is	 only	 used	 to	 draw	 UML	 diagrams	 for	 the	
technical	members	of	the	team,	then	it	is	not	contributing	to	the	creative	collaboration	at	the	
heart	of	DDD.

Domain	 experts	 should	 object	 to	 terms	 or	 structures	 that	 are	 awkward	 or	 inadequate	 to	
convey	domain	understanding;	developers	should	watch	for	ambiguity	or	inconsistency	that	
will	trip	up	design.

With	 a	 ubiquitous	 language,	 the	model	 is	 not	 just	 a	 design	 artifact.	 It	 becomes	 integral	 to	
everything	the	developers	and	domain	experts	do	together

**Use	the	model	as	the	backbone	of	a	language.	Commit	the team	to	exercising	that	language	relentlessly	 in	 all	 communication	 within	 the	 team	 and	 in	 the	 code.	 Within	 a	 bounded	context,	use	the	same	language	in	diagrams,	writing,	and	especially	speech.**

**Recognize	that	a	change	in	the	language	is	a	change	to	the	model.**

**Iron	out	difficulties	by	experimenting	with	alternative	expressions,	which	reflect	alternative	models.	Then	refactor	the	code,	renaming	classes,	methods,	and	modules	to	conform	to	the	new	 model.	 Resolve	 confusion	 over	 terms	 in	 conversation,	 in	 just	 the way	 we	 come	 to	agree	on	the	meaning	of	ordinary	words**

### Continuous	Integration

*Once	a	bounded	context	has	been	defined,	we	must	keep	it	sound.*

**Institute	a	process	of	merging	all	code	and	other	implementation	artifacts	frequently,	with	
automated	 tests	 to	 flag	 fragmentation	 quickly.	 Relentlessly	 exercise	 the	 ubiquitous	
language	 to	 hammer	 out	a	 shared	 view	 of	 the	model	as	 the	 concepts	 evolve	in	 different	
people’s	heads**

### Model-Driven	Design

*Tightly	 relating	 the	 code	 to	 an	 underlying	 model	 gives	 the	 code	 meaning	 and	 makes	 the	
model	relevant.*

**Design	a	portion	of	the	software	system	to	reflect	the	domain	model	in	a	very	literal	way,	
so	 that	 mapping	 is	 obvious.	 Revisit	 the	 model	 and	 modify	 it	 to	 be	 implemented	 more	
naturally	in	software,	even	as	you	seek	to	make	it	reflect	deeper	insight	into	the	domain.	
Demand	a	single	model	that	serves	both	purposes	well,	in	addition	to	supporting	a	 fluent	
ubiquitous	language.**

### Hands-on	Modelers

**Any	technical	person	contributing	to	the	model	must	spend	some	time	touching	the	code,	
whatever	 primary	 role	 he	 or	 she	 plays	 on	 the	 project.	 Anyone	 responsible	 for	 changing	
code	must	learn	to	express	a	model	through	the	code.	Every	developer	must	be	involved	in	
some	 level	 of	 discussion	 about	 the	 model	 and	 have	 contact	 with	 domain	 experts.	 Those	
who	contribute	in	different	ways	must	consciously	engage	those	who	touch	the	code	in	a	
dynamic	exchange	of	model	ideas	through	the	ubiquitous	language.**

### Refactoring	Toward	Deeper	Insight


## II. Building	Blocks	of a Model-Driven	Design

### Layered	Architecture

In	 an	 object-oriented	 program,	 UI,	 database,	 and	 other	 support	 code	 often	 gets	 written	
directly	into	the	business	objects.	Additional	business	logic	is	embedded	in	the	behavior	of	UI	
widgets	and	database	scripts.	This	happens	because	it	is the	easiest	way	to	make	things	work,	
in	the	short	run.	

**Isolate	 the	 expression	 of	 the	 domain	 model	 and	 the	 business	 logic,	 and	 eliminate	 any	dependency	on	infrastructure,	user	interface,	or	even	application	logic	that	is	not	business	logic.	Partition	a	 complex	program	into	layers.	Develop	a	design	within	 each	layer	 that	is	cohesive	and	that	depends	only	on	the	layers	below.	Follow	standard	architectural	patterns	to	 provide	 loose	 coupling	 to	 the	 layers	 above.	 Concentrate	 all	 the	 code	 related	 to	 the	domain	 model	 in	 one	 layer	 and	 isolate	 it	 from	 the	 user	 interface,	 application,	 and	infrastructure	code.	The	domain	objects,	free	of	the	responsibility	of	displaying	themselves,	storing	themselves,	managing	application	tasks,	and	so	forth,	can	be	focused	on	expressing	the	 domain	model.	This	allows	a	model	 to	 evolve	 to	 be	 rich	 enough	and	 clear	 enough	 to	capture	essential	business	knowledge	and	put	it	to	work.**

**The	key	goal	here	is	isolation.**	Related	patterns,	such	as	“Hexagonal	Architecture”	may	serve	
as	 well	 or	 better	 to	 the	 degree	 that	 they	 allow	 our	 domain	 model	 expressions	 to	 avoid	
dependencies	on	and	references	to	other	system	concerns.

### Entities

**When	an	object	is	distinguished	by	its	identity,	rather	than	its	attributes,	make	this	primary	
to	 its	 definition	 in	 the	 model.	 Keep	 the	 class	 definition	 simple	 and	 focused	 on	 life	 cycle	
continuity	and	identity.**

**Define	a	means	of	distinguishing	each	object	 regardless	of	its	 form	or	history.	Be	alert	 to	requirements	 that	 call	 for	 matching	 objects	 by	 attributes.	 Define	 an	 operation	 that	 is	guaranteed	to	produce	a	unique	result	for	each	object,	possibly	by	attaching	a	symbol	that	is	guaranteed	unique.	This	means	of	identification	may	come	from	the	outside,	or	it	may	be	an	arbitrary	identifier	created	by	and	for	the	system,	but	it	must	correspond	to	the	identity	distinctions	in	the	model.**

**The	model	must	define	what	it	means	to	be	the	same	thing.**

### Value	Objects

**When	you	care	only	about	the	attributes	and	logic	of	an	element	of	the	model,	classify	it	as	a	value	object.	Make	it	express	the	meaning	of	the	attributes	it	conveys	and	give	it	related	functionality.	 Treat	 the	 value	 object	 as	 immutable.	 Make	 all	 operations	 Side-effect-free	Functions	 that	don’t	depend	on	any	mutable	state.	Don’t	give	a	value	object	any	identity	and	avoid	the	design	complexities	necessary	to	maintain entities.**

### Domain	Events

*Something	happened	that	domain experts	care	about.*

An	entity is	responsible	 for	 tracking	its	state	and	 the	rules	regulating	its	lifecycle.	But	if	you	
need	to	know	the	actual	causes	of	the	state	changes,	this	is	typically	not	explicit,	and	it	may	
be	difficult	to	explain	how	the	system	got	the	way	it	is.	Audit	trails	can	allow	tracing,	but	are	
not	 usually	 suited	 to	 being	 used	 for	 the	 logic	 of	 the	 program	 itself.	 Change	 histories	 of	
entities	 can	 allow	 access	 to	 previous	 states,	 but	 ignores	 the	meaning	 of	 those	 changes,	 so	
that	any	manipulation	of	the	information	is	procedural,	and	often	pushed	out	of	the	domain	
layer

**Model	information	about	activity	in	 the	 domain	as	a	 series	 of	 discrete	 events.	Represent	each	event	as	a	domain	object.	These	are	distinct	 from	system	events	that	reflect	activity	within	 the	 software	 itself,	 although	 often	 a	 system	 event	 is	 associated	 with	 a	 domain	event,	either	as	part	of	a	response	to	the	domain	event	or	as	a	way	of	carrying	information	about	the	domain	event	into	the	system.**

**A	domain	event	is	a	full-fledged	part	of	the	domain	model,	a representation	of	something	that	happened	in	 the	domain.	Ignore	irrelevant	domain	activity	while	making	 explicit	 the	events	 that	 the	 domain	 experts	 want	 to	 track or	 be	 notified	 of,	 or	 which	 are	 associated	with	state	change	in	the	other	model	objects.**

Domain	events	are	 ordinarily	 immutable,	as	 they	are	a	 record	 of	 something	 in	 the	 past.	In	addition	to	a	description	of	the	event,	a	domain	event	typically	contains	a	timestamp	for	the	time	 the	 event	 occurred and	 the	 identity	 of	 entities	 involved	 in	 the	 event.	 Also,	 a	 domain	event	often	has	a	separate	timestamp	indicating	when	the	event	was	entered	into	the	system	and	the	identity	of	the	person	who	entered	it.	When	useful,	an	identity	for	the	domain	event	can	be	based	on	some	set	of	these	properties.	So,	for	example,	if	two	instances	of	the	same	event	arrive	at	a	node	they	can	be	recognized as	the	same.

### Services

*Sometimes,	it	just	isn’t	a	thing.*

Some	 concepts	 from	 the	 domain	 aren’t	 natural	 to	 model	 as	 objects.	 Forcing	 the	 required	domain	 functionality	 to	 be	 the	 responsibility	 of	 an	 entity	 or	 value	 either	 distorts	 the	definition	of	a	model-based	object	or	adds	meaningless	artificial	objects.	

**When	a	significant	process	or	transformation	in	the	domain	is	not	a	natural	responsibility	of	 an	 entity	 or	 value	 object,	 add	 an	 operation	 to	 the	 model	 as	 a	 standalone	 interface	declared	as	a	service.	Define	a	service	contract,	a	set	of	assertions	about	interactions	with	the	service.	(See	assertions.)	State	these	assertions	in	the	ubiquitous	language	of	a	specific	bounded	 context.	 Give	 the	 service	 a	 name,	 which	 also	 becomes	 part	 of	 the	 ubiquitous	language.**

### Modules

Everyone	 uses	modules,	 but	 few	 treat	 them	 as	 a	 full-fledged	 part	 of	 the	model.	 Code	 gets	
broken	 down	 into	 all	 sorts	 of	 categories,	 from	 aspects	 of	 the	 technical	 architecture	 to	developers’	 work	 assignments.	 Even	 developers	 who	 refactor	 a	 lot	 tend	 to	 content themselves	with	modules	conceived	early	in	the	project.

**Choose	modules	 that	 tell	 the	story	of	 the	system	and	contain	a	cohesive	set	of	concepts.	Give	the modules	names	that	become	part	of	the	ubiquitous	language.	Modules	are	part	of	the	model	and	their	names	should	reflect	insight	into	the	domain.**

**This	often	yields	low	coupling	between	modules,	but	if	it	doesn’t	look	for	a	way	to	change	the	model	to	disentangle	the	concepts,	or	an	overlooked	concept	that might	be	the	basis	of	a	module	that	would	bring	the	elements	together	in	a	meaningful	way.	Seek	low	coupling	in	the	sense	of	concepts	that	can	be	understood	and	reasoned	about	independently.	Refine	the	model	until	it	partitions	according	to	high-level	domain	concepts	and	the	corresponding	code	is	decoupled	as	well.**

### Aggregates


It	 is	 difficult	 to	 guarantee	 the	 consistency	 of	 changes	 to	 objects	 in	 a	 model	 with	 complex	associations.	Objects	are	supposed	to	maintain	their	own	internal	consistent	state,	but	they	can	 be	 blindsided	 by	 changes	 in	 other	 objects	 that	 are	 conceptually	 constituent	 parts.	Cautious	 database	 locking	 schemes	 cause	 multiple	 users	 to	 interfere	 pointlessly	 with	 each	other	and	can make	a	system	unusable.	Similar	issues	arise	when	distributing	objects	among	multiple	servers,	or	designing	asynchronous	transactions.

**Cluster	the	entities	and	value	objects	into	aggregates	and	define	boundaries	around	each.	Choose	 one	 entity	 to	 be	 the	 root	 of	 each	 aggregate,	 and	 allow	 external	 objects	 to	 hold	references	 to	 the	 root	 only	 (references	 to	 internal	members	 passed	 out	 for	 use	 within	 a	single	operation	only).	Define	properties	and	invariants	 for	 the	aggregate	as	a	whole	and	give	enforcement	responsibility	to	the	root	or	some	designated	framework	mechanism.**

Use	the	same	aggregate	boundaries	to	govern	transactions	and	distribution.

Within	 an	 aggregate	 boundary,	 apply	 consistency	 rules	 synchronously.	 Across	 boundaries,	
handle	updates	asynchronously.

Keep	 an	 aggregate	 together	 on	 one	 server.	 Allow	 different	 aggregates	 to	 be	 distributed	
among	nodes.	

### Repositories

*Query	access	to	aggregates	expressed	in	the	ubiquitous	language.*

Proliferation	 of	 traversable	associations	 used	 only	 for	 finding	 things	muddles	 the	model.	In	mature	models,	queries	often	express	domain	concepts.	Yet	queries	can	cause	problems.

The	 sheer	 technical	 complexity	 of	 applying	 most	 database	 access	 infrastructure	 quickly	
swamps	 the	 client	 code,	 which	 leads	 developers	 to	 dumb-down	 the	 domain	 layer,	 which	
makes	the	model	irrelevant

A	query	framework	may	encapsulate	most	of	that	technical	complexity,	enabling	developers	
to	pull	the	exact	data	they	need	from	the	database	in	a	more	automated	or	declarative	way,	
but	that	only	solves	part	of	the	problem.

Unconstrained	 queries	 may	 pull	 specific	 fields	 from	 objects,	 breaching	 encapsulation,	 or	
instantiate	a	few	specific	objects	from	the	interior	of	an	aggregate,	blindsiding	the	aggregate	
root	and	making	 it	 impossible	 for	 these	 objects	 to	enforce	 the	 rules	 of	 the	 domain	model.	
Domain	 logic	 moves	 into	 queries	 and	 application	 layer	 code,	 and	 the	 entities	 and	 value	
objects	become	mere	data	containers.

**For	each	type of	aggregate	that	needs	global	access,	create	a	service	that	can	provide	the	illusion	of	an	in-memory	collection	of	all	objects	of	that	aggregate’s	root	type.	Set	up	access	through	a	well-known	global	interface.	Provide	methods	to	add	and	remove	objects,	which	will	encapsulate	the	actual	insertion	or	removal	of	data	in	the	data	store.	Provide	methods	that	 select	 objects	 based	 on	 criteria	 meaningful	 to	 domain	 experts.	 Return	 fully	instantiated	 objects	 or	 collections	 of	 objects	 whose	 attribute	 values	 meet	 the	 criteria,	thereby	encapsulating	the	actual	storage	and	query	technology,	or	return	proxies	that	give	the	 illusion	 of	 fully	 instantiated	 aggregates	 in	 a	 lazy	 way.	 Provide	  repositories	 only	 for aggregate	 roots	 that	 actually	 need	 direct	 access.	 Keep	 application	 logic	 focused	 on	 the	model,	delegating	all	object	storage	and	access	to	the	repositories.**

### Factories	

When	creation	of	an	entire,	internally	consistent	aggregate,	or	a	large	value	object,	becomes	
complicated	or	reveals	too	much	of	the	internal	structure,	factories	provide	encapsulation.

Creation	of	an	object	can	be	a	major	operation	in	itself,	but	complex	assembly	operations	do	
not	fit	the	responsibility	of	the	created	objects.	Combining	such	responsibilities	can	produce	
ungainly	designs	that	are	hard	to	understand.	Making	the	client	direct	construction	muddies	
the	design	of	 the	client,	breaches	encapsulation	of	 the	assembled	object	or	aggregate,	and	
overly	couples	the	client	to	the	implementation	of	the	created	object.

**Shift	 the	 responsibility	 for	 creating	 instances	 of	 complex	 objects	 and	 aggregates	 to	 a	separate	 object,	 which	 may	 itself	 have	 no	 responsibility	 in	 the	 domain	 model	 but	 is	 still	part	of	the	domain	design.	Provide	an	interface	that	encapsulates	all	complex	assembly	and	that	 does	 not	 require	 the	 client	 to	 reference	 the	 concrete	 classes	 of	 the	 objects	 being	instantiated.	 Create	 an	 entire	 aggregate	 as	 a	 piece,	 enforcing	 its	 invariants.	 Create	 a	complex	value	object	as	a	piece,	possibly	after	assembling	the	elements	with	a	builder.**

## III. Supple	Design

+ Making	behavior	obvious
+ Reducing	the	cost	of	change
+ Creating	software	developers	to	work	with

### Intention-Revealing	Interfaces

**Name	classes	and	operations	to	describe	their	effect	and	purpose,	without	reference	to	the	means	by	which	they	do	what	they	promise.	This	relieves	the	client	developer	of	the	need	to	 understand	 the	 internals.	 These	 names	 should	 conform	 to	 the	 ubiquitous	 language	 so	that	 team	 members	 can	 quickly	 infer	 their	 meaning.	 Write	 a	 test	 for	 a	 behavior	 before	creating	it,	to	force	your	thinking	into	client	developer	mode.**

### Side-Effect-Free	Functions

**Place	as	much	of	the	logic	of	the	program	as	possible	into	functions,	operations	that	return	results	with	no	observable	side	effects.	Strictly	segregate	commands	(methods	which	result	in	modifications	to	observable	state)	into	very	simple	operations	that	do	not	return	domain	information.	Further	control	side	effects	by	moving	complex	logic	into	value	objects	when	a	concept	fitting	the	responsibility	presents	itself.All	operations	of	a	value	object	should	be	side-effect-free	functions.**

### Assertions

When	 the	 side	 effects	 of	 operations	 are	 only	 defined	 implicitly	 by	 their	 implementation,	
designs	 with	 a	 lot	 of	 delegation	 become	 a	 tangle	 of	 cause	 and	 effect.	 The	 only	 way	 to	
understand	 a	 program	 is	 to	 trace	 execution	 through	 branching	 paths.	 The	 value	 of	
encapsulation	is	lost.	The	necessity	of	tracing	concrete	execution	defeats	abstraction.

**State	post-conditions	of	operations	and	invariants	of	classes	and	aggregates.	If	assertions	cannot	 be	 coded	 directly	 in	 your	 programming	 language,	 write	 automated	 unit	 tests	 for	them.	Write	 them	into	documentation	or	diagrams	where	it	 fits	 the	 style	of	 the	project’s	development	process.**

Seek	models	 with	 coherent	 sets	 of	 concepts,	 which	 lead	 a	 developer	 to	 infer	 the	 intended	
assertions,	accelerating	the	learning	curve	and	reducing	the	risk	of	contradictory	code.

Assertions	define	contracts	of	services	and	entity	modifiers.

Assertions	define	invariants	on	aggregates.

### Standalone	Classes

Even	within	a	module,	the	difficulty	of	interpreting	a	design	increases	wildly	as	dependencies	
are	 added.	 This	 adds	 to	 mental	 overload,	 limiting	 the	 design	 complexity	 a	 developer	 can	
handle.	Implicit	concepts	contribute	to	this	load	even	more	than	explicit	references.

**Low	coupling	is	fundamental	to	object	design.	When	you	can,	go	all	the	way.	Eliminate	all	other	concepts	 from	the	picture.	Then	the	class	will	be	completely	self-contained	and	can	be	 studied	 and	 understood	 alone.	 Every	 such	 self-contained	 class	 significantly	 eases	 the	burden	of	understanding	a	module.**

### Closure	of	Operations

Most	interesting	objects	end	up	doing	things	that	can’t	be	characterized	by	primitives	alone.

**Where	 it	 fits,	 define	 an	 operation	 whose	 return	 type	 is	 the	 same	 as	 the	 type	 of	 its	argument(s).	 If	 the	 implementer	 has	 state	 that	 is	 used	 in	 the	 computation,	 then	 the	implementer	 is	 effectively	 an	 argument	 of	 the	 operation,	 so	 the	 argument(s)	 and	 return	value	 should	be	of	 the	 same	 type	as	 the	implementer.	Such	an	operation	is	closed	under	the	set	of	instances	of	that	type.	A	closed	operation	provides	a	high-level	interface	without	introducing	any	dependency	on	other	concepts.**

This	pattern	is	most	often	applied	to	the	operations	of	a	value	object.	Because	the	life	cycle	
of	an	entity	has	significance	in	the	domain,	you	can’t	just	conjure	up	a	new	one	to	answer	a	
question.	 There	 are	 operations	 that	 are	 closed	 under	 an	 entity	 type.	 You	 could	 ask	 an	
Employee	 object	 for	 its	 supervisor	and	get	 back	another	Employee.	 But	 in	general,	entities	
are	not	the	sort	of	concepts	that	are	likely	to	be	the	result	of	a	computation.	So,	for	the	most	
part,	this	is	an	opportunity	to	look for	in	the	value	objects.

You	sometimes	get	halfway	to	this	pattern.	The	argument	matches	the	implementer,	but	the	
return	 type	 is	 different,	 or	 the	 return	 type	 matches	 the	 receiver	 and	 the	 argument	 is	
different.	 These	 operations	 are	 not	 closed,	 but	 they	 do	 give	 some	 of	 the	 advantage	 of	
closure,	in	freeing	the	mind.

### Declarative	Design

#### A	Declarative	Style	of	Design

### Drawing	on	Established	Formalisms
有些公用的domain，可以直接抽象出来，比如account和role，比如数学

### Conceptual	Contours

**Decompose	design elements	(operations,	interfaces,	classes,	and	aggregates)	into	cohesive	units,	 taking	 into	 consideration	 your	 intuition	 of	 the	 important	 divisions	 in	 the	 domain.	Observe	 the	axes	of	change	and	stability	 through	successive	 refactorings	and	look	 for	 the	underlying	conceptual	contours	that	explain	these	shearing	patterns.	Align	the	model	with	the	consistent	aspects	of	 the	domain	 that	make	it	a	viable	area	of	knowledge	in	 the	 first	place.**

## IV Context	Mapping	for	Strategic Design

1. bounded	context:A	description	of	a	boundary	 (typically	a	subsystem,	or	the	work	of	a	particular	team)	within	which	a	particular	model	is	defined	and	applicable.
2. upstream-downstream:A	relationship	 between	 two	 groups	 in	 which	 the	 “upstream”	 group’s	 actions	 affect	 project	success	of	the	“downstream”	group,	but	the	actions	of	the	downstream	do	not	significantly	affect	 projects	 upstream.	 (e.g.	 If	 two	 cities	 are	 along	 the	 same	 river,	 the	 upstream	 city’s	pollution	primarily	affects	the	downstream	city.).The	upstream	team	may	succeed	independently	of	the	fate	of	the	downstream	team.
3. mutually	dependent:A	situation	in	which	 two	software	development	projects	in	separate	contexts	must	both	be	delivered	 in	 order	 for	 either	 to	 be	 considered	 a	 success.
4. free:A	 software	 development	 context	 in	 which	 the	 direction,	success	 or	 failure	 of	 development	work	in	other	contexts	has	little	effect	on	delivery.

### Context	Map

**Identify	each	model	in	play	on	the	project	and	define	its	bounded	context.	This	includes	the	implicit	 models	 of	 non-object-oriented	 subsystems.	 Name	 each	 bounded	 context,	 and	make	the	names	part	of	the	ubiquitous	language.**

**Describe	 the	 points	 of	 contact	 between	 the	models,	 outlining	 explicit	 translation	 for	 any	communication,	highlighting	any	sharing,	isolation	mechanisms,	and	levels	of	influence.**

**Map	the	existing	terrain.	Take	up	transformations	later.**

### Partnership *

*When teams	 in	 two	 contexts	 will	 succeed	 or	 fail	 together,	 a	 cooperative	 relationship	 often	emerges。*

**Where	 development	 failure	 in	 either	 of	 two	 contexts	 would	 result	 in	 delivery	 failure	 for	both,	 forge	 a	 partnership	 between	 the	 teams	 in	 charge	 of	 the	 two	 contexts.	 Institute	 a	process	for	coordinated	planning	of	development	and	joint	management	of	integration.**

**The teams	 must	 cooperate	 on	 the	 evolution	 of	 their	 interfaces	 to	 accommodate	 the	development	needs	of	both	systems.	Interdependent	features	should	be	scheduled	so	that	they	are	completed	for	the	same	release.**

### Shared	Kernel

*Sharing	 a	 part	 of	 the	model	 and	 associated	 code	is	 a	very	intimate	interdependency,	which	can	leverage	design	work	or	undermine	it.*

**Designate	 with	 an	 explicit	 boundary	 some	 subset	 of	 the	 domain	 model	 that	 the	 teams	agree	to	share.	Keep	this	kernel	small.**

**Within	this	boundary,	include,	along	with	this	subset	of	the	model,	the	subset	of	code	or	of	the	database	design	associated	with	that	part	of	the	model.	This	explicitly	shared	stuff	has	special	status,	and	shouldn’t	be	changed	without	consultation	with the	other	team.**

### Customer/Supplier	Development

*When	 two	 teams	 are	 in	 an	 upstream-downstream	 relationship,	 where	 the	 upstream	 team	may	 succeed	 independently	 of	 the	 fate	 of	 the	 downstream	 team,	 the	 needs	 of	 the	downstream	come	to	be	addressed	in	a	variety	of	ways	with	a	wide	range	of	consequences.*

**Establish	 a	 clear	 customer/supplier	 relationship	 between	 the	 two	 teams,	 meaning	downstream	 priorities	 factor	 into	 upstream	 planning.	 Negotiate	 and	 budget	 tasks	 for	downstream	requirements	so	that	everyone	understands	the	commitment	and	schedule.**

Agile	teams	can	make	the	downstream	team	play	the	customer	role	to	the	upstream	team,	in	
planning	sessions.		Jointly	developed	automated	acceptance	tests	can	validate	the	expected	
interface	from	the	upstream.	Adding	these	tests	to	the	upstream	team’s	test	suite,	to	be	run	
as	part	of	its	continuous	integration,	will	 free	 the	upstream	 team	 to	make	changes	without	
fear	of	side	effects	downstream.

### Conformist

**Eliminate	the	complexity	of	translation	between	bounded	contexts	by	slavishly	adhering	to	the	 model	 of	 the	 upstream	 team.	 Although	 this	 cramps	 the	 style	 of	 the	 downstream	designers	 and	 probably	 does	 not	 yield	 the	 ideal	 model	 for	 the	 application,	 choosing	conformity	 enormously	 simplifies	 integration.	 Also,	 you	 will	 share	 a	 ubiquitous	 language	with	 your	 upstream	 team.	 The	 upstream	 is	 in	 the	 driver’s	 seat,	 so	 it	 is	 good	 to	 make	communication	easy	for	them.	Altruism	may	be	sufficient	to	get	them	to	share	information	with	you.**

### Anticorruption	Layer

**As	a	downstream	client,	create	an	isolating	layer	to	provide	your	system	with	functionality	of	the	upstream	system	in	terms	of	your	own	domain	model.	This	layer	talks	to	the	other	system	through	its	existing	interface,	requiring	little	or	no	modification	to	the	other	system.	Internally,	 the	 layer	 translates	 in	 one	 or	 both	 directions	 as	 necessary	 between	 the	 two	models.**

### Open-host	Service

**Define	 a	 protocol	 that	 gives	 access	 to	 your	 subsystem	 as	 a	 set	 of	 services.	 Open	 the	protocol	 so	 that	 all	 who	 need	 to	 integrate	 with	 you	 can	 use	 it.	 Enhance	 and	 expand	 the	protocol	 to	 handle	 new	 integration	 requirements,	 except	 when	 a	 single	 team	 has	idiosyncratic	needs.	Then,	use	a	one-off	translator	to	augment	the	protocol	for	that	special	case	so	that	the	shared	protocol	can	stay	simple	and	coherent.**

### Published	Language

**Use	 a	 well-documented	 shared	 language	 that	 can	 express	 the	 necessary	 domain	information	as	a	common	medium	of	communication,	translating	as	necessary	into	and out	of	that	language.**

### Separate	Ways

**Declare	a	bounded	context	to	have	no	connection	to	the	others	at	all,	allowing	developers	to	find	simple,	specialized	solutions	within	this	small	scope.**

### Big	Ball	of	Mud *

**Draw	a	boundary	around	the	entire	mess	and	designate	it	a	big	ball	of	mud.	Do	not	try	to	apply	sophisticated	modeling	within	this	context.	Be	alert	to	the	tendency	for	such	systems	to	sprawl	into	other	contexts.**

## V. Distillation	for	Strategic	Design

How	do	you	focus	on	your	central	problem	and	keep	from	drowning	in	a	sea	of	side	issues?

Distillation	is	the	process	of	separating	the	components	of	a	mixture	to	extract	the	essence	in	
a	 form	that	makes	it	more	valuable	and	useful.	A	model	is	a	distillation	of	knowledge.	With	
every	 refactoring	 to	 deeper	 insight,	 we	 abstract	 some	 crucial	 aspect	 of	 domain	 knowledge	
and	 priorities.	 Now,	 stepping	 back	 for	 a	 strategic	 view,	 this	 chapter	 looks	 at	 ways	 to	
distinguish	broad	swaths	of	the	model	and	distill	the	domain	model	as	a	whole.	

### Core	Domain

It	 is	 harsh	 reality	 that	 not	 all	 parts	 of	 the	 design	 are	 going	 to	 be	equally	 refined.	 Priorities	
must	be	set.	To	make	 the	domain	model	an	asset,	 the	critical	core	of	 that	model	has	 to	be	
sleek	 and	 fully	 leveraged	 to	 create	 application	 functionality.	 But	 scarce,	 highly	 skilled	
developers	tend	to	gravitate	to	technical	infrastructure	or	neatly	definable	domain	problems	
that	can	be	understood	without	specialized	domain	knowledge.

**Boil	the	model	down.	Define	a	core	domain	and	provide	a	means	of	easily	distinguishing	it	from	 the	 mass	 of	 supporting	 model	 and	 code.	 Bring	 the	 most	 valuable	 and	 specialized	concepts	into	sharp	relief.	Make	the	core	small.**

**Apply	top	talent	to	the	core	domain,	and	recruit	accordingly.	Spend	the	effort	in	the	core	to	find	 a	 deep	 model	 and	 develop	 a	 supple	 design—sufficient	 to	 fulfill	 the	 vision	 of	 the	system**

### Generic	Subdomains

Some	 parts	 of	 the	 model	 add	 complexity	 without	 capturing	 or	 communicating	 specialized	
knowledge.	Anything	extraneous	makes	the	core	domain	harder	to	discern	and	understand.	
The	 model	 clogs	 up	 with	 general principles	 everyone	 knows	 or	 details	 that	 belong	 to	
specialties	which	are	not	your	primary	focus	but	play	a	supporting	role.	Yet,	however	generic,	
these	other	elements	are	essential	to	the	functioning	of	the	system	and	the	full	expression	of	
the	model.

**Identify	 cohesive	 subdomains	 that	 are	 not	 the	 motivation	 for	 your	 project.	 Factor	 out	generic	models	of	these	subdomains	and	place	them	in	separate	modules.	Leave	no	trace	of	your	specialties	in	them.**

**Once	they	have	been	separated,	give	their	continuing	development	lower	priority	than	the	core	domain,	and	avoid	assigning	your	core	developers	to	the	tasks	(because	they	will	gain	little	 domain	 knowledge	 from	 them).	 Also	 consider	 off-the-shelf	 solutions	 or	 published	models	for	these	generic	subdomains.**

### Domain	Vision	Statement

At	the	beginning	of	a	project,	the	model	usually	doesn’t	even	exist,	yet	the	need	to	focus	its	
development	 is	 already	 there.	 In	 later	 stages	 of	 development,	 there	 is	 a	 need	 for	 an	
explanation	of	the	value	of	the	system	that	does	not	require	an	in-depth	study	of	the	model.	
Also,	 the	critical	aspects	of	 the	domain	model	may	span	multiple	bounded	contexts,	but	by	
definition	these	distinct	models	can’t	be	structured	to	show	their	common	focus.

**Write	a	short	description	(about	one	page)	of	the	core	domain	and	the	value	it	will	bring,	the	 “value	 proposition.”	 Ignore	 those	 aspects	 that	 do	 not	 distinguish	 this	 domain	 model	from	 others.	Show	 how	 the	 domain	model	 serves	and	 balances	 diverse	interests.	 Keep	it	narrow.	Write	this	statement	early	and	revise	it	as	you	gain	new	insight.**

## Highlighted	Core

*A	 domain	 vision	 statement	 identifies	 the	 core	 domain	 in	 broad	 terms,	 but	 it	 leaves	 the	identification	 of	 the	 specific	 core	 model	 elements	 up	 to	 the	 vagaries	 of	 individual	interpretation.	Unless	there	is	an	exceptionally	high	level	of	communication	on	the	team,	the	vision	statement	alone	will	have	little	impact.*

**Write	a	very	brief	document	(three	to	seven	sparse	pages)	that	describes	the	core	domain	and	the	primary	interactions	among	core	elements.**

**Flag	the	elements	of	the	core	domain	within	the	primary	repository	of	the	model,	without	particularly	trying	to	elucidate	its	role.	Make	it	effortless	for	a	developer	to	know	what	is	in	or	out	of	the	core**

*Although	 the	 vision	 statement	 and	 highlighted	 core	 inform	 and	 guide,	 they	 do	 not	 actually	modify	the	model	or	the code	itself.	Partitioning	generic	subdomains	physically	removes	some	distracting	elements.	Next	we’ll	look	at	other	ways	to	structurally	changethe	model	and	the	design	itself	to	make	the	core	domain	more	visible	and	manageable.*

### Cohesive	Mechanisms

Computations	 sometimes	 reach	 a	 level	 of	 complexity	 that	 begins	 to	 bloat	 the	 design.	 The	
conceptual	“what”	is	swamped	by	 the	mechanistic	“how.”	A	large	number	of	methods	 that	
provide	algorithms	for	resolving	the	problem	obscure	the	methods	that	express	the problem.

**Partition	 a	 conceptually	 cohesive	 mechanism	 into	 a	 separate	 lightweight	 framework.	Particularly	watch	for	formalisms	or	well-documented	categories	of	algorithms.	Expose	the	capabilities	 of	 the	 framework	 with	 an	 intention-revealing	 interface.	 Now	 the	 other	elements	 of	 the	 domain	 can	 focus	 on	 expressing	 the	 problem	 (“what”),	 delegating	 the	intricacies	of	the	solution	(“how”)	to	the	framework.**

**Factoring	 out	 generic	 subdomains	 reduces	 clutter,	 and	 cohesive	 mechanisms	 serve	 to	encapsulate	 complex	 operations.	 This	 leaves	 behind	 a	 more	 focused	 model,	 with	 fewer	distractions	that	add	no	particular	value	to	the	way	users	conduct	their	activities.	But	you	are	unlikely	ever	to	find	good	homes	for	everything	in	the	domain	model	that	is	not	core.	The segregated	core	takes	a	direct	approach	to	structurally	marking	off	the	core	domain**

### Segregated	Core

Elements	 in	 the	 model	 may	 partially	 serve	 the	 core	 domain	 and	 partially	 play	 supporting	
roles.	Core	elements	may	be	tightly	coupled	to	generic	ones.	The	conceptual	cohesion	of	the	
core	 may	 not	 be	 strong	 or	 visible.	 All	 this	 clutter	 and	 entanglement	 chokes	 the	 core.	
Designers	can’t	clearly	see	the	most	important	relationships,	leading	to	a	weak	design.

**Refactor	 the	 model	 to	 separate	 the	 core	 concepts	 from	 supporting	 players	 (including	 illdefined	ones)	and	strengthen	the	cohesion	of	the	core	while	reducing	its	coupling	to	other	code.	 Factor	 all	 generic	 or	 supporting	 elements	 into	 other	 objects	 and	 place	 them	 into	other	 packages,	 even	 if	 this	 means	 refactoring	 the	 model	 in	 ways	 that	 separate	 highly	coupled	elements.**

### Abstract	Core

Even	the	core	domain	model	usually	has	so	much	detail	that	communicating	the	big	picture	can	be	difficult.

When	 there	 is	 a	 lot	 of	 interaction	 between	 subdomains	 in	 separate	 modules,	 either	 many	
references	will	have	to	be	created	between	modules,	which	defeats	much	of	the	value	of	the	
partitioning,	 or	 the	 interaction	 will	 have	 to	 be	 made	 indirect,	 which	 makes	 the	 model	
obscure.

**Identify	the	most	fundamental	differentiating	concepts	in	the	model	and	factor	them	into	distinct	 classes,	 abstract	 classes,	 or	 interfaces.	 Design	 this	 abstract	 model	 so	 that	 it	expresses	 most	 of	 the	 interaction	 between	 significant	 components.	 Place	 this	 abstract	overall	model	in	its	own module,	while	the	specialized,	detailed	implementation	classes	are	left	in	their	own	modules	defined	by	subdomain.**

## VI. Large-scale	Structure	for	Strategic	Design

In	a	large	system	without	any	overarching	principle	that	allows	elements	to	be	interpreted	in
terms	of	their	role	in	patterns	that	span	the	whole	design,	developers	cannot	see	the	forest	
for	 the	 trees.	We	need	 to	be	able	 to	understand	 the	role	of	an	individual	part	in	 the	whole	
without	delving	into	the	details	of	the	whole.

A	 “large-scale	 structure”	 is	 a	 language	 that	 lets	 you	 discuss	 and	 understand	 the	 system	 in	
broad	strokes.	A	set	of	high-level	concepts	or	rules,	or	both,	establishes	a	pattern	of	design	
for	an	entire	system.	This	organizing	principle	can	guide	design	as	well	as	aid	understanding.	
It	helps	coordinate	independent	work	because	 there	is	a	shared	concept	of	 the	big	picture:	
how	the	roles	of	various	parts	shape	the	whole.

**Devise	a	pattern	of	rules	or	roles	and	relationships	that	will	span	the	entire	system	and	that	allows	 some	 understanding	 of	 each	 part’s	 place	 in	 the	 whole—even	 without	 detailed	knowledge	of	the	part’s	responsibility**

### Evolving	Order

Design	free-for-alls	produce	systems	no	one	can	make	sense	of	as	a	whole,	and	they	are	very	
difficult	 to	 maintain.	 But	 architectures	 can	 straitjacket	 a	 project	 with	 up-front	 design	
assumptions	 and	 take	 too	 much	 power	 away	 from	 the	 developers/designers	 of	 particular	
parts	of	the	application.	Soon,	developers	will	dumb	down	the	application	to	fit	the	structure,	
or	 they	 will	 subvert	 it	 and	 have	 no	 structure	 at	 all,	 bringing	 back	 the	 problems	 of	
uncoordinated	development.

**Let	this	conceptual	large-scale	structure	evolve	with	the	application,	possibly	changing	to	a	completely	 different	 type	 of	 structure	 along	 the	 way.	 Don’t	 over	 constrain	 the	 detailed	design	and	model	decisions	that	must	be	made	with	detailed	knowledge**

**Large-scale	structure	should	be	applied	when	a	structure	can	be	found	that	greatly	clarifies	the	 system	 without	 forcing	 unnatural	 constraints	 on	model	 development.	 Because	 an	 illfitting	 structure	 is	 worse	 than	 none,	 it	 is	 best	 not	 to	 shoot	 for	 comprehensiveness,	 but	rather	to	find	a	minimal	set	that	solves	the	problems	that	have	emerged.	Less	is	more.**

**What	 follows	 is	 a	 set	 of	 four	 particular	 patterns	 of	 large-scale	 structure	 that	 emerge	 on	some	projects	and	are	representative	of	this	kind	of	pattern.**

### System	Metaphor

Metaphorical	thinking	is	pervasive	in	software	development,	especially	with	models.	But	the	
Extreme	Programming	practice	of	“metaphor”	has	come	to mean	a	particular	way	of	using	a	
metaphor	to	bring	order	to	the	development	of	a	whole	system.

Software	designs	tend	to	be	very	abstract	and	hard	to	grasp.	Developers	and	users	alike	need	
tangible	ways	to	understand	the	system	and	share	a	view	of	the	system	as	a	whole.	

**When	 a	 concrete	 analogy	 to	 the	 system	 emerges	 that	 captures	 the	 imagination	 of	 team	members	 and	 seems	 to	 lead	 thinking	 in	 a	 useful	 direction,	 adopt	 it	 as	 a	 large-scale	structure.	 Organize	 the	 design	 around	 this	 metaphor	 and	 absorb	 it	 into	 the	 ubiquitous	language.	 The	 system	 metaphor	 should	 both	 facilitate	 communication	 about	 the	 system	and	 guide	 development	 of	 it.	 This	 increases	 consistency	 in	 different	 parts	 of	 the	 system,	potentially	even	across	different	bounded	contexts.	But	because	all	metaphors	are	inexact,	continually	reexamine	the	metaphor	for	overextension	or	inaptness,	and	be	ready	to	drop	it	if	it	gets	in	the	way.**

### Responsibility	Layers

in	 object-oriented	 design,	 individual	 objects	 are	 assigned	 narrow	 sets	 of	 related	responsibilities.	Responsibility-driven	design	also	applies	to	larger	scales.

When	 each	 individual	 object	 has	 handcrafted	 responsibilities,	 there	 are	 no	 guidelines,	 no	
uniformity,	and	no	ability	to	handle	large	swaths	of	the	domain	together.	To	give	coherence	
to	 a	 large	 model,	 it	 is	 useful	 to	 impose	 some	 structure	 on	 the	 assignment	 of	 those	
responsibilities.	

**Look	at	 the	conceptual	dependencies	in	your	model	and	 the	varying	 rates	and	 sources	of	change	of	different	parts	of	your	domain.	If	you	identify	natural	strata	in	the	domain,	cast	them	 as	 broad	 abstract	 responsibilities.	 These	 responsibilities	 should	 tell	 a	 story	 of	 the	high-level	 purpose	 and	 design	 of	 your	 system.	 Refactor	 the	 model	 so	 that	 the	responsibilities	 of	 each	 domain	 object,	 aggregate,	 and	 module	 fit	 neatly	 within	 the	responsibility	of	one	layer.**

### Knowledge	Level

A	group	of	objects	that	describe	how	another	group	of	objects	should	behave.	

In	 an	 application	 in	 which	 the	 roles	 and	 relationships	 between	 entities	 vary	 in	 different	
situations,	complexity	can	explode.	Neither	fully	general	models	nor	highly	customized	ones	
serve	 the	users’	needs.	Objects	end	up	with	 references	 to	other	 types	 to	cover	a	variety	of	
cases,	or	with	attributes	 that	are	used	in	different	ways	in	different	 situations. Classes	 that	
have	 the	 same	 data	 and	 behavior	 may	 multiply	 just	 to	 accommodate	 different	 assembly	
rules.

**Create	a	distinct	set	of	objects	that	can	be	used	to	describe	and	constrain	the	structure	and	behavior	 of	 the	 basic	 model.	 Keep	 these	 concerns	 separate	 as	 two	 “levels,”	 one	 very	concrete,	 the	 other	 reflecting	 rules	 and	 knowledge	 that	 a	 user	 or	 super-user	 is	 able	 to	customize.**

### Pluggable	Component	Framework

Opportunities	arise	in	a	very	mature	model	that	is	deep	and	distilled.	A	pluggable	component	
framework	 usually	 only	 comes	 into	 play	 after	 a	 few	 applications	 have	 already	 been	
implemented	in	the	same	domain.

When	a	variety	of	applications	have	to	interoperate,	all	based	on	the	same	abstractions	but	
designed	independently,	translations	between	multiple	bounded	contexts	limit	integration.	A	
shared	 kernel	 is	 not	 feasible	 for	 teams	 that	 do	 not	 work	 closely	 together.	 Duplication	 and	
fragmentation	raise	costs	of	development	and	installation,	and	interoperability	becomes	very	
difficult.

**Distill	an	abstract	 core	of	interfaces	and	interactions	and	 create	a	 framework	 that	allows	diverse	implementations	 of	 those	interfaces	 to	 be	 freely	 substituted.	 Likewise,	allow	any	application	to	use	those	components,	so	long	as	it	operates	strictly	through	the	interfaces	of	the	abstract	core.**

