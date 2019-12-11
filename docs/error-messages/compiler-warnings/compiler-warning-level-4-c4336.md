---
title: Ostrzeżenie kompilatora (poziom 4) C4336
ms.date: 11/04/2016
f1_keywords:
- C4336
helpviewer_keywords:
- C4336
ms.assetid: 93f199dd-d6dd-42c0-82d8-c12d101a7235
ms.openlocfilehash: e83bac9028980bdf3ef7449fbef065a8c9316d2d
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991338"
---
# <a name="compiler-warning-level-4-c4336"></a>Ostrzeżenie kompilatora (poziom 4) C4336

Zaimportuj bibliotekę typów odsyłaczy "type_lib1" przed importem "type_lib2"

Do biblioteki typów odwołuje się dyrektywa [#import](../../preprocessor/hash-import-directive-cpp.md) . Jednak biblioteka typów zawiera odwołanie do innej biblioteki typów, do której nie odwołuje się `#import`. Ten inny plik TLB został znaleziony przez kompilator.

Nadana dwie biblioteki typów na dysku utworzone na podstawie następujących dwóch plików (skompilowane za pomocą MIDL. exe):

```
// c4336a.idl
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12b")]
library c4336aLib
{
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12c")]
   enum E_C4336
   {
      one, two, three
   };
};
```

Druga biblioteka typów:

```
// c4336b.idl
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12d")]
library C4336bLib
{
   importlib ("c4336a.tlb");
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12e")]
   struct S_C4336
   {
      enum E_C4336 e;
   };
};
```

Poniższy przykład generuje C4336:

```cpp
// C4336.cpp
// compile with: /W4 /LD
// #import "C4336a.tlb"
#import "C4336b.tlb"   // C4336, uncomment previous line to resolve
```
