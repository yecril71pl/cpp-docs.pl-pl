---
title: Błąd kompilatora C3366
ms.date: 11/04/2016
f1_keywords:
- C3366
helpviewer_keywords:
- C3366
ms.assetid: efc55bcf-c16d-43c1-a36f-87a6165fa2a8
ms.openlocfilehash: 4d1cd510cda9957ced1d9dd5fd8fea267f39220d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507773"
---
# <a name="compiler-error-c3366"></a>Błąd kompilatora C3366

'Zmienna': statyczne składowe danych zarządzane lub WinRTtypes musi być zdefiniowany w ramach definicji klasy

Podjęto próbę odwołania statycznego elementu członkowskiego klasy WinRT lub .NET lub interfejs poza definicją klasy lub interfejsu.

Kompilator musi wiedzieć, pełna definicja klasy (aby emitować metadane — po jednym przebiegu) i wymaga elementów członkowskich danych statycznych do zainicjowania w klasie.

Na przykład poniższy przykład generuje C3366 i pokazuje, jak go naprawić:

```
// C3366.cpp
// compile with: /clr /c
ref class X {
   public:
   static int i;   // initialize i here to avoid C3366
};

int X::i = 5;      // C3366
```
