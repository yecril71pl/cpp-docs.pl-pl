---
title: Kompilator ostrzeżenie (poziom 1) C4674 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4674
dev_langs:
- C++
helpviewer_keywords:
- C4674
ms.assetid: 638dae0b-b82c-4865-9599-72630827ca09
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9b2f945982e80b49403387241f29a50876274e66
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024882"
---
# <a name="compiler-warning-level-1-c4674"></a>Kompilator ostrzeżenie (poziom 1) C4674

"method" powinien być zadeklarowany jako "static" i mieć dokładnie jeden parametr

Podpis operatora konwersji nie jest poprawny. Metoda nie jest uważany za konwersji zdefiniowanej przez użytkownika. Aby uzyskać więcej informacji na temat definiowania operatorów, zobacz [operatory zdefiniowane przez użytkownika (C + +/ CLI)](../../dotnet/user-defined-operators-cpp-cli.md) i [konwersje zdefiniowane przez użytkownika (C + +/ interfejsu wiersza polecenia)](../../dotnet/user-defined-conversions-cpp-cli.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4674.

```
// C4674.cpp
// compile with: /clr /WX /W1 /LD
ref class G {
   int op_Implicit(int i) {   // C4674
      return 0;
   }
};
```
