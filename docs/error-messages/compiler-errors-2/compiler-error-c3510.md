---
title: Błąd kompilatora C3510
ms.date: 11/04/2016
f1_keywords:
- C3510
helpviewer_keywords:
- C3510
ms.assetid: c48387bc-0300-4a4d-97f7-3fb90f82a451
ms.openlocfilehash: dbb65628aa6e0da94a91a59724ca8e1cd5b56491
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187355"
---
# <a name="compiler-error-c3510"></a>Błąd kompilatora C3510

Nie można zlokalizować biblioteki zależnego typu "type_lib"

[no_registry](../../preprocessor/no-registry.md) i [auto_search —](../../preprocessor/auto-search.md) zostały przekazane do `#import` , ale kompilator nie mógł odnaleźć przywoływanej biblioteki typów.

Aby rozwiązać ten problem, upewnij się, że wszystkie biblioteki typów i bibliotek typu odwołania są dostępne dla kompilatora.

Poniższy przykład spowoduje wygenerowanie C3510:

Założono, że zostały zbudowane następujące dwa typy biblioteki i że C3510a.tlb został usunięty lub nie w ścieżce.

```
// C3510a.idl
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12b")]
library C3510aLib
{
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12c")]
   enum E_C3510
   {
      one, two, three
   };
};
```

A następnie kod źródłowy dla drugiego biblioteki typów:

```
// C3510b.idl
// post-build command: del /f C3510a.tlb
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12e")]
library C3510bLib
{
   importlib ("C3510a.tlb");
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12d")]
   struct S_C3510 {
      enum E_C3510 e;
   };
};
```

A następnie kod klienta:

```
// C3510.cpp
#import "c3510b.tlb" no_registry auto_search   // C3510
int main() {
   C3510aLib::S_C4336 ccc;
}
```