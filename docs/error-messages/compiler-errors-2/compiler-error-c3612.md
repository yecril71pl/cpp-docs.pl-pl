---
title: Błąd kompilatora C3612
ms.date: 11/04/2016
f1_keywords:
- C3612
helpviewer_keywords:
- C3612
ms.assetid: aa6e3a2b-4afa-481c-98c1-1b6d1f82f869
ms.openlocfilehash: ab18381d3f263e3207662e1667ac5c835983412f
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "58781409"
---
# <a name="compiler-error-c3612"></a>Błąd kompilatora C3612

"type": Klasa zapieczętowana nie może być abstrakcyjny

Typy zdefiniowane przy użyciu `value` są zapieczętowane domyślnie i klasa jest klasą abstrakcyjną, o ile nie implementuje wszystkie metody bazowej. Zapieczętowana klasa abstrakcyjna nie może być klasą bazową, ani nie może być utworzone.

Aby uzyskać więcej informacji, zobacz [klas i struktur](../../extensions/classes-and-structs-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3612:

```
// C3612.cpp
// compile with: /clr /c
value struct V: public System::ICloneable {};   // C3612

// OK
value struct V2: public System::ICloneable {
   Object^ Clone();
};
```