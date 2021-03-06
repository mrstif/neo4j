ClassMethods
============






.. toctree::
   :maxdepth: 3
   :titlesonly:


   

   

   




Constants
---------





Files
-----



  * `lib/neo4j/active_rel/persistence.rb:47 <https://github.com/neo4jrb/neo4j/blob/master/lib/neo4j/active_rel/persistence.rb#L47>`_





Methods
-------



.. _`Neo4j/ActiveRel/Persistence/ClassMethods#create`:

**#create**
  Creates a new relationship between objects

  .. code-block:: ruby

     def create(props = {})
       relationship_props = extract_association_attributes!(props) || {}
       new(props).tap do |obj|
         relationship_props.each do |prop, value|
           obj.send("#{prop}=", value)
         end
         obj.save
       end
     end



.. _`Neo4j/ActiveRel/Persistence/ClassMethods#create!`:

**#create!**
  Same as #create, but raises an error if there is a problem during save.

  .. code-block:: ruby

     def create!(*args)
       props = args[0] || {}
       relationship_props = extract_association_attributes!(props) || {}
       new(props).tap do |obj|
         relationship_props.each do |prop, value|
           obj.send("#{prop}=", value)
         end
         obj.save!
       end
     end



.. _`Neo4j/ActiveRel/Persistence/ClassMethods#create_method`:

**#create_method**
  

  .. code-block:: ruby

     def create_method
       creates_unique? ? :create_unique : :create
     end





