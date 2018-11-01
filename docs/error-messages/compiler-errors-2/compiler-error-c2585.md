---
title: Błąd kompilatora C2585
ms.date: 11/04/2016
f1_keywords:
- C2585
helpviewer_keywords:
- C2585
ms.assetid: 05bb1a9c-28fb-4a88-a1b5-aea85ebdee1c
ms.openlocfilehash: 812ab15aacd1f6a215c6a5beb7781983859fe858
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593261"
---
# <a name="compiler-error-c2585"></a>Błąd kompilatora C2585

Jawna konwersja na "type" jest niejednoznaczny

Konwersja typu można utworzyć więcej niż jeden wynik.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny

1. Konwersja z typu klasy lub struktury, oparte na wielokrotne dziedziczenie. Jeśli typ dziedziczy tej samej klasy bazowej więcej niż jeden raz, funkcja konwersji lub operatora, należy użyć rozpoznawania zakresu (`::`) aby określić, które klasy dziedziczone służące do konwersji.

1. Operator konwersji i Konstruktor zdefiniowano wprowadzania tej samej konwersji.