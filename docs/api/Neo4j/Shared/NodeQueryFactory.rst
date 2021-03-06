NodeQueryFactory
================






.. toctree::
   :maxdepth: 3
   :titlesonly:


   

   




Constants
---------





Files
-----



  * `lib/neo4j/shared/query_factory.rb:60 <https://github.com/neo4jrb/neo4j/blob/master/lib/neo4j/shared/query_factory.rb#L60>`_





Methods
-------



.. _`Neo4j/Shared/NodeQueryFactory#base_query`:

**#base_query**
  

  .. code-block:: ruby

     def base_query
       @base_query || Neo4j::Session.current.query
     end



.. _`Neo4j/Shared/NodeQueryFactory#base_query=`:

**#base_query=**
  

  .. code-block:: ruby

     def base_query=(query)
       return if query.blank?
       @base_query = query
     end



.. _`Neo4j/Shared/NodeQueryFactory.create`:

**.create**
  

  .. code-block:: ruby

     def self.create(graph_object, identifier)
       factory = case graph_object
                 when Neo4j::ActiveNode
                   NodeQueryFactory
                 when Neo4j::ActiveRel
                   RelQueryFactory
                 else
                   fail "Unable to find factory for #{graph_object}"
                 end
       factory.new(graph_object, identifier)
     end



.. _`Neo4j/Shared/NodeQueryFactory#graph_object`:

**#graph_object**
  Returns the value of attribute graph_object

  .. code-block:: ruby

     def graph_object
       @graph_object
     end



.. _`Neo4j/Shared/NodeQueryFactory#identifier`:

**#identifier**
  Returns the value of attribute identifier

  .. code-block:: ruby

     def identifier
       @identifier
     end



.. _`Neo4j/Shared/NodeQueryFactory#initialize`:

**#initialize**
  

  .. code-block:: ruby

     def initialize(graph_object, identifier)
       @graph_object = graph_object
       @identifier = identifier.to_sym
     end



.. _`Neo4j/Shared/NodeQueryFactory#query`:

**#query**
  

  .. code-block:: ruby

     def query
       graph_object.persisted? ? match_query : create_query
     end





