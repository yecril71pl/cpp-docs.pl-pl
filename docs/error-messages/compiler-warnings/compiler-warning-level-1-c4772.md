---
title: Ostrzeżenie kompilatora (poziom 1) C4772
ms.date: 11/04/2016
f1_keywords:
- C4772
helpviewer_keywords:
- C4772
ms.assetid: dafe6fd8-9faf-41f5-9d66-a55838742c14
ms.openlocfilehash: 89156b2f29fd21160e6abddc3ecb21efaee6dde1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175137"
---
# <a name="compiler-warning-level-1-c4772"></a>Ostrzeżenie kompilatora (poziom 1) C4772

> \#zaimportować przywoływany typ z brakującej biblioteki typów; "*Brak typu*" używany jako symbol zastępczy

Do biblioteki typów odwołuje się dyrektywa [#import](../../preprocessor/hash-import-directive-cpp.md) . Jednak biblioteka typów zawiera odwołanie do innej biblioteki typów, do której nie odwołuje się `#import`. Kompilator nie znalazł tego innego pliku. tlb.

Należy zauważyć, że kompilator nie będzie znajdował bibliotek typów w różnych katalogach, jeśli do określenia tych katalogów jest używany program [/i (Dodatkowe katalogi dołączane)](../../build/reference/i-additional-include-directories.md) . Jeśli chcesz, aby kompilator znalazł biblioteki typów w różnych katalogach, Dodaj te katalogi do zmiennej środowiskowej PATH.

Domyślnie to ostrzeżenie jest wysyłane jako błąd. Nie można pominąć C4772 z/W0.

## <a name="example"></a>Przykład

Jest to pierwsza biblioteka typów wymagana do odtworzenia C4772.

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

Jest to druga biblioteka typów wymagana do odtworzenia C4772.

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
