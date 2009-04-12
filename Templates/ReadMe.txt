LINQ to SQL templates for T4
============================

Known Issues
------------
1.  Tables with CRLF or " in the name break code generation.
2.  Escaping a column or table name with [] but not the association reference causes lookup failure.
3.  Enum's not supported as a member type for classes


Change Log
----------
0.81	TBA		Better error for missing DBML file
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
0.75	26-Sep-2008	Ensure Name is emitted for the Column attribute when it is different from Member
0.74	25-Sep-2008	Use primary key of ths/other table when association doesn't specify this/other key
0.73	25-Sep-2008	Fixed missing namespace in DBML = no namespace declaration (was "MyApplication")
			Renamed L2ST4.tt to L2ST4.ttinclude to make installation easier
			(If you wish to have T4 editor highlighting, rename it to TT and clear the Custom Tool property)
0.72	23-Sep-2008	Fixed stored procedures that take no arguments
0.71	22-Sep-2008	Fixed IsForeignKey attribute in VB.NET version - was negated
0.70	18-Sep-2008	Implemented stored procedures for insert/update/delete
