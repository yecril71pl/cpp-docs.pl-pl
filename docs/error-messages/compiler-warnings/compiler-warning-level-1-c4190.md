---
title: Ostrzeżenie kompilatora (poziom 1) C4190
ms.date: 11/04/2016
f1_keywords:
- C4190
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
ms.openlocfilehash: 6d110aa70a470382e274546e95599804fa3bc7d6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199878"
---
# <a name="compiler-warning-level-1-c4190"></a>Ostrzeżenie kompilatora (poziom 1) C4190

"Identifier1" ma określone powiązanie C, ale zwraca UDT "identifier2", które jest niezgodne z C

Funkcja lub wskaźnik do funkcji ma typ UDT (zdefiniowany przez użytkownika, który jest klasą, strukturą, wyliczeniem lub Unią) jako zwracany typ i `extern` "C" powiązania. Jest to dozwolone, jeśli:

- Wszystkie wywołania tej funkcji występują z C++.

- Definicja funkcji znajduje się w C++.

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
