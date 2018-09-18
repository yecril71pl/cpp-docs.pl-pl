---
title: Błąd kompilatora C2585 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2585
dev_langs:
- C++
helpviewer_keywords:
- C2585
ms.assetid: 05bb1a9c-28fb-4a88-a1b5-aea85ebdee1c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ec7b1e9c1e5e7894740cc80f9c030fa1ee26ec0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028847"
---
# <a name="compiler-error-c2585"></a>Błąd kompilatora C2585

Jawna konwersja na "type" jest niejednoznaczny

Konwersja typu można utworzyć więcej niż jeden wynik.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny

1. Konwersja z typu klasy lub struktury, oparte na wielokrotne dziedziczenie. Jeśli typ dziedziczy tej samej klasy bazowej więcej niż jeden raz, funkcja konwersji lub operatora, należy użyć rozpoznawania zakresu (`::`) aby określić, które klasy dziedziczone służące do konwersji.

1. Operator konwersji i Konstruktor zdefiniowano wprowadzania tej samej konwersji.