<!-- vim-markdown-toc GFM -->

* [Namespace Declarations](#namespace-definitions)
	* [Example: Basic namespace usage](#example-basic-namespace-usage)
   * [Example: Advanced namespace usage](#example-advanced-namespace-usage)

<!-- vim-markdown-toc -->

# Namespace Declarations

Namespaces enclose a region of code, making it so that everything external to
that region—that isn't in a region with an identical name—must refer to the
namespace before referring to whatever is contained within.

All code not explicitly placed in a namespace is considered to be in a root
scope which is shared between every file. Because of this it's important to
give all namespaces in the scope namespace a unique name.

All identifiers are valid for namespaces, none are explicitly disallowed
currently, but if you use certain identifiers that are used by Aeon then
Altazimuth will 100% definitely yell at you.

Interal namespaces that Aeon
already uses are `EE`, and `Math`. Avoid other namespaces that sound like they
could be general or internal like `Game`, `Script`, etc.

A namespace is formed with the syntax:
```cpp
namespace Identifier
{
   $[Namespace-content...]$
}
```

Namespaces are also able to be declared within other namespaces.

## Example: Basic namespace usage

This example is somewhat contrived, as it is not suggested for a single mod to
have multiple namespaces declared in the root scope without good reason.

```cpp
namespace A
{
   // Entities in the same namespace see each other normally.
   void function() { variable++; }
   int variable;
}

namespace B
{
   // Entities in different namespaces don't immediately see each other and can
   // reuse the same name without causing name conflicts. By using the scoping
   // operator the entity from the desired namespace can be explicitly informed.
   void function() { A::function(); }
}
```

## Example: Advanced namespace usage

This example is also contrived, due to a variable and function being declared
in the root scope.

```cpp
int x;

namespace MyCoolMod
{
   int var;

   // You can further sub-group things by declaring
   // namespaces within other namespaces.
   namespace EnemyStuff
   {
      int var;

      void DoSomething()
      {
         // Accessing variable in parent namespace requires specifying the
         // scope if an entity in a child namespace uses the same name:
         var = MyCoolMod::var;

         // Accessing the global scope's x and assigning it to the parent
         // namespace's x requires using the scoping operator with no name
         // before it:
         MyCoolMod::x = ::var;
      }
   }

   namespace MobjStuff
   {
      void DoSomething() { EnemyStuff::DoSomething(); }
   }
}

void RandomFunction()
{
   // Access variable in a nested namespace requires
   // a fully qualified scope specifier.
   int var = Parent::Child::var;
}
```

<!-- EOF -->
