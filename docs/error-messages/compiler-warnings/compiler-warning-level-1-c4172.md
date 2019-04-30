---
title: Kompilator ostrzeżenie (poziom 1) C4172
ms.date: 11/04/2016
f1_keywords:
- C4172
helpviewer_keywords:
- C4172
ms.assetid: a8d2bf65-d8b1-4fe3-8340-a223d7e7fde6
ms.openlocfilehash: caa71da9182c1da1d17d87d901084d0ee9badf73
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391793"
---
# <a name="compiler-warning-level-1-c4172"></a>Kompilator ostrzeżenie (poziom 1) C4172

zwracanie adresu lokalnej zmiennej lub tymczasowej

Funkcja zwraca adres obiektu lokalnej zmiennej lub tymczasowej. Zmienne lokalne i obiekty tymczasowe są niszczony, kiedy funkcja zwraca, więc zwrócony adres jest nieprawidłowy.

Zmodyfikowanie funkcji, tak aby nie zwróci adresu lokalnego obiektu.

Poniższy przykład spowoduje wygenerowanie C4172:

```
// C4172.cpp
// compile with: /W1 /LD
float f = 10;

const double& bar() {
// try the following line instead
// const float& bar() {
   return f;   // C4172
}
```