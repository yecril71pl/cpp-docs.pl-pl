---
title: Ostrzeżenie kompilatora (poziom 1) C4190
ms.date: 11/04/2016
f1_keywords:
- C4190
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
ms.openlocfilehash: 8187926f2477a4d3f1ca3019cc8c3c71710c1dff
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233304"
---
# <a name="compiler-warning-level-1-c4190"></a>Ostrzeżenie kompilatora (poziom 1) C4190

"Identifier1" ma określone powiązanie C, ale zwraca UDT "identifier2", które jest niezgodne z C

Funkcja lub wskaźnik do funkcji ma typ UDT (zdefiniowany przez użytkownika, który jest klasą, strukturą, wyliczeniem lub Unią) jako zwracany typ i `extern "C"` powiązania. Jest to dozwolone, jeśli:

- Wszystkie wywołania tej funkcji występują w języku C++.

- Definicja funkcji jest w języku C++.

## <a name="example"></a>Przykład

```cpp
// C4190.cpp
// compile with: /W1 /LD
struct X
{
   int i;
   X ();
   virtual ~X ();
};

extern "C" X func ();   // C4190
```
