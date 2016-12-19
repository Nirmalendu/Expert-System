
Tourism expert system tells the user which place they can visit in India based on their preferences. At each instance the user is presented with options, selecting an options drives the flow of the expert system.
The user has to reply with the index of the option to interact with the expert system.
The expert system is based on predicate logic, after each question some predicates in the database will become true, the potential results keep getting pruned at each stage. At the end the user is presented with all such cities they would want to visit based on their preferences.

An example run of the expert system:-

* The system is started with a call to main predicate

* User replies with the index of his preferred choice

* User is presented with another question to prune the list of cities from the database, the user replies a choice, this process is repeated until she/he gets a recommendation from the system.


Dissecting the above operations, the modules can be divided into: 
Greeting the user
Asking the user their preferences
Enumerating the options
Reading the options
Evaluating the predicates specified in the rules from the database
Displaying the results, and result exploration

Greeting the user:
A simple write statement is used for greeting.

Asking the user their preferences:
The ask function does the job, for asking the user question from the database is chosen, the first question asked is trip_purpose as it’s the first predicate in every fact in the database. Further questions are asked based on what predicate is being evaluated.

Enumerating the options:
A recursive function enumerates the the options presented for easy input.
The first index is 0, goes till the last.

Reading the options:
The index is read using a simple read method.
Parsing is done i.e. the indexth option is read using a parse function,
the index is used to extract the first atom from the list of choices, until the indexth element is reached or all options are exhausted, if all options are exhausted the user has given a wrong input i.e. it wasn't in the list of options.
This response is saved as the answer, this progress is stored so that the answer doesn’t backtracks, it saves the current position i.e. answer to that specific question.

Evaluating the predicates specified in the rules from the database:
Showing by example:

How a result is evaluated the first call to find_place(place) looks at the first rule in the system place(ladakh), to evaluate this predicate it checks predicate trip_purpose(religious) since this is the first predicate in place(ladakh), the predicate ask asks the user a question presents him with options, the selected option is saved in the progress in the database as a fact using asserta keyword.
If the user replies as above in the example, the fact stored in the system becomes progress(trip_purpose,wildlife), this causes place(ladakh) to become false, now the place where this predicate is satisfied is checked for line by line through the rules, once its found in place(kolkata) the next condition is evaluated, the predicate wildlife_region(east), this goes similarly, since the user enters his preference for east India, the predicate place(kolkata) is true, now the describe(kolkata) predicate would give a description of the place, over here it’s Kolkata.

Displaying the results, and result exploration:

If more than one predicate satisfies the user’s preference, the user can look into his options by pressing the next key, until the list of such places is exhausted, when this happens the user is returned false .

Next gives the immediate next predicate which evaluates true, 10, 100, 1,000, give the next 10, 100, 1,000 places which satisfied the predicates.