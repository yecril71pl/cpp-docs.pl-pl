---
title: Błąd kompilatora C3914
ms.date: 11/04/2016
f1_keywords:
- C3914
helpviewer_keywords:
- C3914
ms.assetid: 8f3190e6-ee50-4916-9ecc-3b8748b2e1e7
ms.openlocfilehash: e7c04da2b7574d3af0e1c05ae4adc3ad513faa0b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577903"
---
# <a name="compiler-error-c3914"></a>Błąd kompilatora C3914

Domyślna właściwość nie może być statyczna

Domyślna właściwość została zadeklarowana niepoprawnie.  Aby uzyskać więcej informacji, zobacz [porady: użycie właściwości w języku C + +/ interfejsu wiersza polecenia](../../dotnet/how-to-use-properties-in-cpp-cli.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C3914 i pokazuje, jak go naprawić.

```
// C3914.cpp
// compile with: /clr /c
ref struct X {
   static property int default[int] {   // C3914
   // try the following line instead
   // property int default[int] {
      int get(int) { return 0; }
      void set(int, int) {}
   }
};
```