-------
ALIASES
-------

I have a long command to type. Can I make it shorter?

.. code-block::

   # ~/.bashrc or ~/.bash_profile

   alias ll="ls -al"

Now when I run ``ll`` in the terminal, it runs ``ls -al`` behind the
scenes.

How can I apply this to my own worklow?

I often run the same commands:

- ``git add .``
- ``git commit --amend --no-edit``

I can use an alias to combine these into one command:

.. code-block::

   # ~/.bashrc or ~/.bash_profile (same as above example)

   alias add-commit='git add . ; git commit --amend --no-edit'

Now, I can ``add-commit``.

Features
--------

- You can view the defined aliases with ``alias``.
- You get tab-completion for free.
- Aliases can be combined. (Aliases can call previously-defined aliases.)

Limitations
-----------

Aliases don't accept parameters.

If you want to create a shortcut that can accept parameters, you'll need a Bash function or a script.

How To Use
----------

Aliases can be defined in ``~/.bashrc`` or ``~/.bash_profile``.

Let's assume you're using ``~./bash_profile`` for this case:

- Define your alias in: ``~/.bash_profile``.
- Save and close ``~/.bash_profile``.
- run ``source ~/.bash_profile`` in the terminal.

You can use tab-completion once an alias has been defined.

Run ``alias`` to list the known aliases. Your new alias should show up in this list.

Run ``alias <name-of-alias>`` to get output specific to a certain alias.


Some Useful Aliases I've Defined
--------------------------------

Here are some annotated sample aliases from my ``~/.bash_profile``:

.. code-block::

   # What branch am I currently on?

   alias branch='git branch --show-current'


   # Add and commit in one step :)

   alias add-commit='git add . ; git commit --amend --no-edit '


   # Pushes the latest to staging

   alias stage='git push origin -f $( branch ) ; '


   # These assume I'm on a branch ready for backports:

   alias bp5.0='git checkout -b $(branch)-v5.0-backport upstream/v5.0'
   alias bp4.4='git checkout -b $(branch)-v4.4-backport upstream/v4.4'
   alias bp4.2='git checkout -b $(branch)-v4.2-backport upstream/v4.2'
   alias bp4.0='git checkout -b $(branch)-v4.0-backport upstream/v4.0'


Resources:
==========

Walkthrough / Tutorial:
----------------------

https://dev.to/ama/a-developer-s-way-of-using-shell-aliases-2ba6

Obligatory SO Post:
------------------

https://stackoverflow.com/questions/7131670/make-a-bash-alias-that-takes-a-parameter

Definitive Reference:
--------------------

https://tldp.org/LDP/abs/html/aliases.html
