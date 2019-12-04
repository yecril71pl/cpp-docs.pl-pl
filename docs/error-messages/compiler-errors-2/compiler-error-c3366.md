---
title: Błąd kompilatora C3366
ms.date: 11/04/2016
f1_keywords:
- C3366
helpviewer_keywords:
- C3366
ms.assetid: efc55bcf-c16d-43c1-a36f-87a6165fa2a8
ms.openlocfilehash: 5173b1c0df7de6a4e8d9993e680b961a82bb10a7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738469"
---
# <a name="compiler-error-c3366"></a>Błąd kompilatora C3366

"zmienna": statyczne składowe danych zarządzane lub WinRTtypes muszą być zdefiniowane w ramach definicji klasy

Podjęto próbę odwołania się do statycznego elementu członkowskiego klasy WinRT lub lub interfejsu platformy .NET poza definicją tej klasy lub interfejsu.

Kompilator musi znać pełną definicję klasy (do emisji metadanych po jednym przebiegu) i wymaga zainicjowania statycznych elementów członkowskich danych w klasie.

Na przykład poniższy przykład generuje C3366 i pokazuje, jak go naprawić:

```cpp
// C3366.cpp
// compile with: /clr /c
ref class X {
   public:
   static int i;   // initialize i here to avoid C3366
};

int X::i = 5;      // C3366
```
