---
title: Błąd kompilatora C3519
ms.date: 11/04/2016
f1_keywords:
- C3519
helpviewer_keywords:
- C3519
ms.assetid: ca24b2bc-7e90-4448-ae84-3fedddf9bca7
ms.openlocfilehash: e9a998e1c3a6c2fb770fb9d26d97b8a24e5554d3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360037"
---
# <a name="compiler-error-c3519"></a>Błąd kompilatora C3519

"invalid_param": nieprawidłowy parametr dla atrybutu embedded_idl

Parametr został przekazany do `embedded_idl` atrybutu [#import](../../preprocessor/hash-import-directive-cpp.md), ale kompilator nie rozpoznał parametru.

Tylko parametry, które są dozwolone w przypadku `embedded_idl` są `emitidl` i `no_emitidl`.

Poniższy przykład spowoduje wygenerowanie C3519:

```
// C3519.cpp
// compile with: /LD
[module(name="MyLib2")];
#import "C:\testdir\bin\importlib.tlb" embedded_idl("no_emitidcl")
// C3519
#import "C:\testdir\bin\importlib.tlb" embedded_idl("no_emitidl")
// OK
```