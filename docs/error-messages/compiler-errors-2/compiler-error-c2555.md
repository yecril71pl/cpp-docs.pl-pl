---
title: Błąd kompilatora C2555
ms.date: 11/04/2016
f1_keywords:
- C2555
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
ms.openlocfilehash: ebf3e4a3aff48311edd5fb95b01a7b2d23990231
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202427"
---
# <a name="compiler-error-c2555"></a>Błąd kompilatora C2555

"Class1:: function1": przesłanianie typu zwracanego funkcji wirtualnej różni się i nie jest współwariantem z "'klasa:: function2"

Funkcja wirtualna i pochodna funkcja przesłaniania mają identyczne listy parametrów, ale różne typy zwracane. Funkcja zastępująca w klasie pochodnej nie może się różnić od funkcji wirtualnej w klasie bazowej tylko przez jej typ zwracany.

Aby rozwiązać ten problem, należy rzutować wartość zwracaną po wywołaniu funkcji wirtualnej.

Ten błąd może również pojawić się w przypadku kompilowania za pomocą/CLR.   Na przykład Wizualizacja C++ odpowiada następującej C# deklaracji:

```
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);
```

is

```
Guid CheckSources(Guid sourceID, Guid carouselIDs[]) [];
```

Poniższy przykład generuje C2555:

```cpp
// C2555.cpp
// compile with: /c
struct X {
   virtual void func();
};
struct Y : X {
   char func();  // C2555
   void func2();   // OK
};
```
