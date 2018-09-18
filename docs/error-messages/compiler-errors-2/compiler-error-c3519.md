---
title: Błąd kompilatora C3519 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3519
dev_langs:
- C++
helpviewer_keywords:
- C3519
ms.assetid: ca24b2bc-7e90-4448-ae84-3fedddf9bca7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ac9c1bfe01cee659ae8b637df23a86315b5310f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46072787"
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