- What are some non-iterator methods for arrays and when are they used?
	- compact
	    - takes away the nil values from an array
	- count
	    - count number of elements in an array
	- include?
	    - checks if an element is in an array
	- flatten
	    - collapses sub-arrays into a normal one
	- a lot more….
	    - a lot more things…..
- List the main iterator methods for arrays and tell when you use each one.
	- each
	    - used for side effects
	- map/collect
	    - manipulate each object in an array with a block
	- find
	    - finds the first element in an array for which the block returns true
	- select/detect
	    - selects all the elements for which the block returns true
- Objects
    - why have objects instead of hashes?
	- They can have much more descriptive and can more easily structure representations of real-life objects
    - what is the difference between using a getter method and just referencing the instance variable?
	- A getter method can be used to retrieve information about an attribute outside of the class when a new instance is created.
    - Should a method that finds the correct user by name (find_by_name?) be a class method or an instance method? Why?
	- Instance level. because we will be looking for self inside of an @@all array(assuming this is a User class).
    - how does initialize work in an object?
	- it sets instance attributes to certain values that are either given as a default or input each time for a new instance
    - what two methods will attr_accessor :name write?
	- def name
	    @name
	  end
	- def name=(name)
	    @name = name
	  end
-Object relations
      Books, Authors, and Genres
    - Draw out the relations between the objects
	-  books belong to an author and a genre. authors have many books and have many genres through books. genres will have many books and many authors through books.
    - Which object is going to act as my join - and thus store the data?
	- books
    - Write out the three classes with the belongs to relations
	- class Author
	    attr_accessor :books
	  end
	- class Book
	    attr_accessor :author, :genre
	  end
	- class Genre
	    attr_accessor :books
	  end
    - write a method that will give me a list of books written by an author(inside books)
	- def books_by_author(author)
	    @@all.select { |book| book.author == author }
	  end
    - write a method that will give me a list of all genre’s of an author(inside books)
	- def genres_by_author(author)
	    author_books  = @@all.select { |book| book.author == author }
	    author_books.map { |book| book.genre } .uniq
	  end


		
