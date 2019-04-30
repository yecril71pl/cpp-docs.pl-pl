---
title: Kompilator ostrzeżenie (poziom 1) C4674
ms.date: 11/04/2016
f1_keywords:
- C4674
helpviewer_keywords:
- C4674
ms.assetid: 638dae0b-b82c-4865-9599-72630827ca09
ms.openlocfilehash: f7db2f37224a8defffb545b0cfaf018fd4654227
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374550"
---
# <a name="compiler-warning-level-1-c4674"></a>Kompilator ostrzeżenie (poziom 1) C4674

"method" powinien być zadeklarowany jako "static" i mieć dokładnie jeden parametr

Podpis operatora konwersji nie jest poprawny. Metoda nie jest uważany za konwersji zdefiniowanej przez użytkownika. Aby uzyskać więcej informacji na temat definiowania operatorów, zobacz [operatory zdefiniowane przez użytkownika (C++sposób niezamierzony)](../../dotnet/user-defined-operators-cpp-cli.md) i [konwersje zdefiniowane przez użytkownika (C++sposób niezamierzony)](../../dotnet/user-defined-conversions-cpp-cli.md).

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
