---
layout: post
title:      "Abstraction: attr_accessors & Active Record"
date:       2018-07-25 01:54:01 +0000
permalink:  abstraction_attr_accessors_and_active_record
---

I think that now I am at a level where I appreciate abstraction *a lot* more. Consider, for example, our beloved `attr_accessor`s that come right after defining a class:

```
class Whale
  attr_accessor :baleen, :blue, :grey, :narwhal
end
```

The code above is a much shorter way of abstracting the setter and getter methods for each attribute. In the long and very repetitive version, we would encounter this exact code:

```
def baleen=(baleen)
  @baleen = baleen
end

def baleen
  @baleen
end

def blue=(blue)
  @blue = blue
end

def blue
  @blue
end

def grey=(grey)
  @grey = grey
end

def grey
  @grey
end

def narwhal=(narwhal)
  @narwhal = narwhal
end

def narwhal
  @narwhal
end

```

Similarly, when transitioning to object-relational mapping (ORM), I noted the repetitive inquiry of the attributes, again:

```
class Gamer
  attr_accessor :id, :username, :rank
	
  def self.new_from_db(row)
	  # create a new Gamer object given a row from the database
		new_gamer = self.new
		new_gamer.id = row[0]
		new_gamer.username = row[1]
		new_gamer.rank = row[2]
		
		new_gamer
  end
end
```
Here, we're not only calling `new_gamer` 5 times, we are repeating the `attr_accessor`s to make sure they are mapped correctly to the three rows in the database.

And these are only 3 attributes we are talking about here, which is nowhere close to how many a real application would normally have.

What if we could build our `attr_accessor`s from abstract column names? Well, that is where dynamic ORMs come in, tall and proud. Dynamic ORMs define methods not tied to any specific class, thus they can be shared among *many* classes.

Telling our code to write code about itself is called metaprogramming, and it is a pretty cool concept, I might say. Consider:

```
class Gamer
  def self.table_name
    #table_name code
  end
 
  def self.column_names
    #column_names code
  end
 
  self.column_names.each do |col_name|
    attr_accessor col_name.to_sym
  end
end
```

By iterating over the `column_names` class method and setting an `attr_accessor` for each one (and not forgetting to convert the `col_name` string into a symbol, as any `attr_accessor` must be a symbol), we are metaprogramming and abstracting the code so that we do not need to ever go back and name each `attr_accessor` separately - no matter how many of them we have.

And the next level of abstraction comes... in a form of library! And it is called Active Record. With the help of this Ruby gem, we get access to the base methods like `.column_names`, `.create`, `.find`, `.save`, and many more. We can **C**reate, **R**ead, **U**pdate and **D**elete (CRUD), i.e., operate on and manipulate data much easier and faster. And it is universal!

(Well, at least, for Ruby it is!)
