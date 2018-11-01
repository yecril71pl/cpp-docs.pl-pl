---
title: Kompilator ostrzeżenie (poziom 1) C4190
ms.date: 11/04/2016
f1_keywords:
- C4190
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
ms.openlocfilehash: 05984594a57878aad8037861a15ac9284ff65192
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50521234"
---
# <a name="compiler-warning-level-1-c4190"></a>Kompilator ostrzeżenie (poziom 1) C4190

"identifier1" ma określone powiązanie C, ale zwraca UDT identifier2, co jest niezgodne z C

Funkcja lub wskaźnikiem do funkcji ma UDT (typ zdefiniowany przez użytkownika, który jest klasy, struktury, wyliczenia lub Unii) jako typ zwracany i `extern` powiązania "C". To jest legalna jeśli:

- Wszystkie wywołania do tej funkcji występują w języku C++.

- Jest definicją funkcji w języku C++.

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