---
title: Błąd kompilatora C2585
ms.date: 11/04/2016
f1_keywords:
- C2585
helpviewer_keywords:
- C2585
ms.assetid: 05bb1a9c-28fb-4a88-a1b5-aea85ebdee1c
ms.openlocfilehash: 57a0cd7a200c5bbb875821eb9e10314d98e58185
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177394"
---
# <a name="compiler-error-c2585"></a>Błąd kompilatora C2585

jawna konwersja na typ "Type" jest niejednoznaczna

Konwersja typu może generować więcej niż jeden wynik.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać ten problem, sprawdzając następujące możliwe przyczyny

1. Konwersja z klasy lub typu struktury na podstawie wielokrotnego dziedziczenia. Jeśli typ dziedziczy tę samą klasę bazową więcej niż raz, funkcja konwersji lub operator musi użyć rozpoznawania zakresu (`::`), aby określić, które klasy dziedziczone mają być używane w konwersji.

1. Operator konwersji i Konstruktor zostały zdefiniowane w taki sam sposób.
