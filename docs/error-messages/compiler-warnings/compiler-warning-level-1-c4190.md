---
title: Kompilator ostrzeżenie (poziom 1) C4190 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4190
dev_langs:
- C++
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d398331c159c6fc639160dbe54d6ab5f969d3dbd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063739"
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