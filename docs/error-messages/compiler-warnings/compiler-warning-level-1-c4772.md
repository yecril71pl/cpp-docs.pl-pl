---
title: Kompilator ostrzeżenie (poziom 1) C4772
ms.date: 11/04/2016
f1_keywords:
- C4772
helpviewer_keywords:
- C4772
ms.assetid: dafe6fd8-9faf-41f5-9d66-a55838742c14
ms.openlocfilehash: 95243ab66d5d0296e1c316ff8dde7add75a030cd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50540026"
---
# <a name="compiler-warning-level-1-c4772"></a>Kompilator ostrzeżenie (poziom 1) C4772

> \#Importuj odwołanie do typu z brakującej biblioteki typów; "*brakuje typu*" używana jako symbol zastępczy

Odwołanie do biblioteki typów z [#import](../../preprocessor/hash-import-directive-cpp.md) dyrektywy. Jednak biblioteka typów zawiera odwołanie do innej biblioteki typów, który nie był przywoływany z `#import`. Nie znaleziono pliku .tlb przez kompilator.

Należy pamiętać, że kompilator nie znajdzie biblioteki typów w różnych katalogach Jeśli używasz [/I (dodatkowe katalogi dołączenia)](../../build/reference/i-additional-include-directories.md) opcję kompilatora, aby określić te katalogi. Jeśli chcesz, aby kompilator, aby znaleźć biblioteki typów w różnych katalogach, należy dodać te katalogi do zmiennej środowiskowej PATH.

Domyślnie to ostrzeżenie jako błąd. Nie można pominąć C4772 z /W0.

## <a name="example"></a>Przykład

Jest to pierwszy wymaganymi do odtworzenia C4772 biblioteki typów.

```IDL
// c4772a.idl
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12b")]
library C4772aLib
{
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c100")]
   enum E_C4772a
   {
      one, two, three
   };
};
```

Jest to potrzebne do odtworzenia C4772 drugi biblioteki typów.

```IDL
// c4772b.idl
// post-build command: del /f C4772a.tlb
// C4772a.tlb is available when c4772b.tlb is built
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12d")]
library C4772bLib
{
   importlib ("c4772a.tlb");
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12e")]
   struct S_C4772b
   {
      enum E_C4772a e;
   };
};
```

Poniższy przykład spowoduje wygenerowanie C4772:

```cpp
// C4772.cpp
// assumes that C4772a.tlb is not available to the compiler
// #import "C4772a.tlb"
#import "C4772b.tlb"   // C4772 uncomment previous line to resolve
                       // and make sure c4772a.tlb is on disk
```