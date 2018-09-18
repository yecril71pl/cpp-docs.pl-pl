---
title: Błąd ewaluatora wyrażeń CXX0065 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0065
dev_langs:
- C++
helpviewer_keywords:
- CAN0065
- CXX0065
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c100b1edbd36f4384e8deb1abf5b36465e8da479
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024167"
---
# <a name="expression-evaluator-error-cxx0065"></a>Błąd CXX0065 programu Expression Evaluator

Zmienna musi ramki stosu

Wyrażenie zawiera zmienną, która istnieje w bieżącym zakresie, ale nie został jeszcze utworzony.

Ten błąd może wystąpić, kiedy ma zmieniana w prologu funkcji, ale nie została jeszcze Konfigurowanie ramki stosu dla funkcji lub jeśli masz schodkowego kod wyjścia dla funkcji.

Przejść przez kod prologu, dopóki nie skonfigurowano ramki stosu przed obliczając wartość wyrażenia.

Ten błąd jest taka sama jak CAN0065.