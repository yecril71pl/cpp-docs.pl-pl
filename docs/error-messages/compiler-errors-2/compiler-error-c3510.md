---
title: Błąd kompilatora C3510 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3510
dev_langs:
- C++
helpviewer_keywords:
- C3510
ms.assetid: c48387bc-0300-4a4d-97f7-3fb90f82a451
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5cc134823abf2657426b0c1be9cfbe6d92a74035
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111335"
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