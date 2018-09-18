---
title: Błąd kompilatora C3366 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3366
dev_langs:
- C++
helpviewer_keywords:
- C3366
ms.assetid: efc55bcf-c16d-43c1-a36f-87a6165fa2a8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b3638ba2415839c044d9a82d82d0abe8bc2c98e2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026507"
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
