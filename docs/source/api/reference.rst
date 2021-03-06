reference
=========
general purpose reference to Lua object in registry
---------------------------------------------------

..  code-block:: cpp
	:caption: reference
		
	class reference;

This type keeps around a reference to something that was on the stack and places it in the Lua registry. It is the backbone for all things that reference items on the stack and needs to keep them around beyond their appearance and lifetime on said Lua stack. Its progeny include :doc:`sol::coroutine<coroutine>`, :doc:`sol::function<function>`, :doc:`sol::<protected_function>`, :doc:`sol::object<object>`, :doc:`sol::table<table>`/:doc:`sol::global_table<table>`, :doc:`sol::<thread>`, and :doc:`sol::userdata<userdata>`.


members
-------

.. code-block:: cpp
	:caption: function: push referred-to element from the stack

	int push() const noexcept;

This function pushes the referred-to data onto the stack and returns how many things were pushed. Typically, it returns 1.

.. code-block:: cpp
	:caption: function: reference value

	int registry_index() const noexcept;

The value of the reference in the registry.

.. code-block:: cpp
	:caption: functions: non-nil, non-null check

	bool valid () const noexcept;
	explicit operator bool () const noexcept;

These functions check if the reference at ``T`` is valid: that is, if it is not :doc:`nil<types>` and if it is not non-existing (doesn't refer to anything, including nil) reference. The explicit operator bool allows you to use it in the context of an ``if ( my_obj )`` context.

.. code-block:: cpp
	:caption: function: retrieves the type

	type get_type() const noexcept;

Gets the :doc:`sol::type<types>` of the reference; that is, the Lua reference.

.. code-block:: cpp
	:caption: function: lua_State* of the reference

	lua_State* lua_state() const noexcept;

Gets the ``lua_State*`` this reference exists in.