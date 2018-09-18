---
title: Błąd ewaluatora wyrażeń CXX0024 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0024
dev_langs:
- C++
helpviewer_keywords:
- CXX0024
- CAN0024
ms.assetid: eca6adbd-8ff2-4f51-a1cc-a2e9d5d0a47d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2816be7bb1d33757d9722d605d461ac6fb34fadd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118198"
---
# <a name="expression-evaluator-error-cxx0024"></a>Błąd CXX0024 programu Expression Evaluator

Operacja wymaga wartości l

Wyrażenie, które nie zostało oszacowane jako l wartością został określony dla operacji, która wymaga wartości l.

L wartością (tzw. ponieważ znajduje się po lewej stronie instrukcji przypisania) jest wyrażeniem, która odwołuje się do lokalizacji w pamięci.

Na przykład `buffer[count]` jest prawidłową wartością l, ponieważ wskazuje lokalizacji pamięci. Porównanie logiczne `zed != 0` nie jest prawidłową wartością l, ponieważ jej wartość PRAWDA lub FAŁSZ, nie daje w wyniku adres pamięci.

Ten błąd jest taka sama jak CAN0024.