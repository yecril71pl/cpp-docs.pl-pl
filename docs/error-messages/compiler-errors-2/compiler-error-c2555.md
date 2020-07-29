---
title: Błąd kompilatora C2555
description: Odwołanie do błędu kompilatora Visual Studio C++ C2555.
ms.date: 03/30/2020
f1_keywords:
- C2555
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
ms.openlocfilehash: ecac92bc663a6344e9ddafe13c194a92ab944c51
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87207800"
---
# <a name="compiler-error-c2555"></a>Błąd kompilatora C2555

> "*Class1*::*function1*": przesłanianie typu zwracanego funkcji wirtualnej różni się i nie jest współwariantem z "*'klasa*::*function2*"

Funkcja wirtualna i pochodna funkcja przesłaniania mają identyczne listy parametrów, ale różne typy zwracane.

## <a name="remarks"></a>Uwagi

W języku C++ funkcja zastępująca w klasie pochodnej nie może się różnić tylko przez zwracany typ z funkcji wirtualnej w klasie bazowej.

Istnieją wyjątki od tej reguły dla określonych typów zwracanych. Gdy Klasa pochodna przesłania publiczną klasę bazową, może zwrócić wskaźnik lub odwołanie do klasy pochodnej zamiast wskaźnika lub odwołania do klasy bazowej. Te typy zwracane są nazywane *współwariantem*, ponieważ różnią się w zależności od typu. Ten wyjątek reguły nie zezwala na typ referencyjny współwariantu na wskaźnik lub wskaźnik do wskaźnika.

Jednym ze sposobów na rozwiązanie błędu jest zwrócenie tego samego typu co Klasa bazowa. Następnie należy rzutować wartość zwracaną po wywołaniu funkcji wirtualnej. Innym jest również zmiana listy parametrów, aby uczynić składową klasy pochodnej funkcję przeciążenia zamiast zastąpienia.

## <a name="examples"></a>Przykłady

Ten błąd może pojawić się w przypadku kompilowania za pomocą **`/clr`** . Na przykład język C++ odpowiada następującej deklaracji języka C#:

```csharp
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);
```

is

```cpp
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

Aby rozwiązać ten problem, Zmień zwracany typ `Y::func` na **`void`** .
