LINQ to SQL templates for T4
============================

Known Issues
------------
1.  Tables with CRLF or " in the name break code generation.
2.  Escaping a column or table name with [] but not the association reference causes lookup failure.

Change Log
----------
0.84			Blocks are now defined with StartHeaderBlock, StartFooterBlock and StartNamedBlock and ended with just EndBlock
			The file splitting class now enforces that blocks do not overlap by throwing if they do instead of mangling output
0.83			Corrected return types for IsComposable functions to be IQueryable or nullable scalars
			IsComposable functions that are IQueryable now correctly call CreateMethodCallQuery 
			Functions and Stored Procs with no return type now correctly type to System.Object
0.82			Column Expression now emitted into attribute
			Column IsReadOnly now generates getters only when serialization is none
			Removed old serialization enum
			Emit KnownType class attribute only when serialization is unidirectional
			AutoSync, IsDbGenerated and UpdateCheck attributes now default based on other attributes
0.81			Better error for missing DBML file
			Tidy-up of comments and formatting in L2ST4.ttinclude
			Options now specified in "var options" in each template
			SerializeDataContractSP1 only takes effect when DBML Serialization Mode is Unidrectional!
			Entity-per-file now implemented via the option switch (uses Manager class)
			Entity-per-file manages the project items/subitems in Visual Studio when in that environment
			Namespaces now taken from Visual Studio project and DBML Custom Tool Namespace as per designer
			EntityBase now supported as the base class for entities
			Fixed namespace/file split for function return type auto-generated classes
			Auto-generated classes now emit Name and CanBeNull in the Column Attribute if required
			Emit the KnownType attribute required for DataContract serialization with inheritance
			Do not emit DataMembers when Serialization is None
			Ensure OnDeserialization is new/Shadows when emitted in subclasses
			Update/Delete entity with SPs ignores retcode - options.StoredProcedureConcurrency to re-enable
			Add enumeration support.
0.80	09-Jan-2009	Licensed under the Microsoft Public License (MsPL)
			IsComposable function support
0.79	11-Dec-2008	Associations managing the relationship fk's now actually do <blush>
			Serialization mode of none doesn't cause compilation errors in EntitySet associations
0.78	07-Dec-2008	Association management code reworked to correctly handle one-to-one and other scenarios
			Insert/Update/Delete method override signatures are now correct and skip partial for it
			IsUnique attribute for associations now emitted
			OnCreated method now only emitted for entities with a primary key
			Delay-loaded column support
			Made many of the property setters private to prevent accidental setting from the template
0.77	17-Nov-2008	IsInheritanceDefault honoured for types in inheritance scenarios
0.76	20-Oct-2008	Default type name to table name if omitted and allow it to be the same without appending "1"
			Remove forcing of primary key on target for isforeignkey associations
			Association lookup for ThisKey & OtherKey is now by Member (not Name) and sequence is preserved
			Now honours access modifier and property modifiers for associations
