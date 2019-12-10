---
title: Ostrzeżenie kompilatora (poziom 4) C4706
ms.date: 11/04/2016
f1_keywords:
- C4706
helpviewer_keywords:
- C4706
ms.assetid: 89cd3f4f-812c-4a4b-9426-65a5a6d1b99c
ms.openlocfilehash: 2ff8794dcf29539b492f53bfdf6f0810988c0f72
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74989908"
---
# <a name="compiler-warning-level-4-c4706"></a>Ostrzeżenie kompilatora (poziom 4) C4706

przypisanie w wyrażeniu warunkowym

Wartość testowa w wyrażeniu warunkowym była wynikiem przypisania.

Przypisanie ma wartość (wartość po lewej stronie przypisania), która może być używana legalnie w innym wyrażeniu, łącznie z wyrażeniem testowym.

Poniższy przykład generuje C4706:

```cpp
// C4706a.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( a  = b ) // C4706
   {
   }
}
```

Ostrzeżenie zostanie przeprowadzone nawet w przypadku podwójnego nawiasu otaczającego warunek testu:

```cpp
// C4706b.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( ( a  =  b ) ) // C4706
   {
   }
}
```

Jeśli zamiarem jest przetestowanie relacji, a nie przypisanie, użyj operatora `==`. Na przykład poniższy wiersz testuje, czy a i b są równe:

```cpp
// C4706c.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( a == b )
   {
   }
}
```

Jeśli zamierzasz, aby wartość testowa była wynikiem przypisania, przetestuj test, aby upewnić się, że przypisanie jest inne niż zero lub nie ma wartości null. Na przykład następujący kod nie spowoduje wygenerowania tego ostrzeżenia:

```cpp
// C4706d.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( ( a = b ) != 0 )
   {
   }
}
```
