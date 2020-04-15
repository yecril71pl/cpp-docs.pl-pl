---
title: Błąd kompilatora C2555
description: Odwołanie do błędu kompilatora Visual Studio C++ C2555.
ms.date: 03/30/2020
f1_keywords:
- C2555
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
ms.openlocfilehash: fe0e6379e783387506e6098c9b14a047baa8e6c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374172"
---
# <a name="compiler-error-c2555"></a>Błąd kompilatora C2555

> '*class1*::*function1*': nadrzędny typ powrotu funkcji wirtualnej różni się i nie jest kowariancją od '*class2*::*function2*'

Funkcja wirtualna i pochodna funkcja zastępowania mają identyczne listy parametrów, ale różne typy zwracane.

## <a name="remarks"></a>Uwagi

W języku C++ funkcja nadrzędna w klasie pochodnej nie może się różnić tylko przez typ zwracany z funkcji wirtualnej w klasie podstawowej.

Istnieje wyjątek od tej reguły dla niektórych typów zwracania. Gdy klasa pochodna zastępuje publiczną klasę podstawową, może zwrócić wskaźnik lub odwołanie do klasy pochodnej zamiast wskaźnika klasy podstawowej lub odwołania. Te typy zwracane są nazywane *kowariancją,* ponieważ różnią się one w zależności od typu. Ten wyjątek reguły nie zezwala na kowariancyjne odwołania do wskaźnika lub wskaźnik do wskaźnika typów.

Jednym ze sposobów rozwiązania błędu jest zwrócenie tego samego typu co klasa podstawowa. Następnie rzutuj wartość zwracaną po wywołaniu funkcji wirtualnej. Innym jest również zmienić listę parametrów, aby pochodna funkcja elementu członkowskiego klasy przeciążenia zamiast zastąpienia.

## <a name="examples"></a>Przykłady

Ten błąd może zostać wyświetlony **`/clr`** podczas kompilowania z . Na przykład C++ równoważne następującej deklaracji Języka C#:

```csharp
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);
```

is

```cpp
Guid CheckSources(Guid sourceID, Guid carouselIDs[]) [];
```

Następujący przykład generuje C2555:

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

Aby to naprawić, zmień `Y::func` typ `void`zwrotu na .
