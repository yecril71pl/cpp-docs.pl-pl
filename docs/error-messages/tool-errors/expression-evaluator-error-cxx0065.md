---
title: Błąd CXX0065 programu Expression Evaluator
ms.date: 11/04/2016
f1_keywords:
- CXX0065
helpviewer_keywords:
- CAN0065
- CXX0065
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
ms.openlocfilehash: 7b62e42da2a74d910e2dc56ce2dfcb5cb38f2bfa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62299325"
---
# <a name="expression-evaluator-error-cxx0065"></a>Błąd CXX0065 programu Expression Evaluator

Zmienna musi ramki stosu

Wyrażenie zawiera zmienną, która istnieje w bieżącym zakresie, ale nie został jeszcze utworzony.

Ten błąd może wystąpić, kiedy ma zmieniana w prologu funkcji, ale nie została jeszcze Konfigurowanie ramki stosu dla funkcji lub jeśli masz schodkowego kod wyjścia dla funkcji.

Przejść przez kod prologu, dopóki nie skonfigurowano ramki stosu przed obliczając wartość wyrażenia.

Ten błąd jest taka sama jak CAN0065.