---
title: "Kompilatora (poziom 1) ostrzeżenie C4772 | Dokumentacja firmy Microsoft"
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: error-reference
f1_keywords:
- C4772
dev_langs:
- C++
helpviewer_keywords:
- C4772
ms.assetid: dafe6fd8-9faf-41f5-9d66-a55838742c14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 631cd4f872c7b8912b791417c04f6c6e9e056bdd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4772"></a>Kompilator C4772 ostrzegawcze (poziom 1)

> \#Importuj odwołuje się do typu z brakującej biblioteki typów; "*Brak typu*" użyty jako element zastępczy

Biblioteki typów odwoływano z [#import](../../preprocessor/hash-import-directive-cpp.md) dyrektywy. Jednak biblioteka typów zawiera odwołanie do innego biblioteki typów, który nie został wywołany `#import`. Nie znaleziono pliku .tlb przez kompilator.

Należy pamiętać, że kompilator nie będzie zawierał biblioteki typów w różnych katalogach, jeśli używasz [/I (dodatkowe katalogi dołączenia)](../../build/reference/i-additional-include-directories.md) opcję kompilatora, aby określić te katalogi. Kompilator, aby znaleźć biblioteki typów w różnych katalogach należy dodać te katalogi do zmiennej środowiskowej PATH.

Domyślnie to ostrzeżenie jako błąd. Nie można pominąć C4772 z /W0.

## <a name="example"></a>Przykład

Jest to pierwszy potrzebne do odtworzenia C4772 biblioteki typów.

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

Poniższy przykład generuje C4772:

```cpp
// C4772.cpp
// assumes that C4772a.tlb is not available to the compiler
// #import "C4772a.tlb"
#import "C4772b.tlb"   // C4772 uncomment previous line to resolve
                       // and make sure c4772a.tlb is on disk
```