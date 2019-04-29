---
title: Błąd CXX0024 programu Expression Evaluator
ms.date: 11/04/2016
f1_keywords:
- CXX0024
helpviewer_keywords:
- CXX0024
- CAN0024
ms.assetid: eca6adbd-8ff2-4f51-a1cc-a2e9d5d0a47d
ms.openlocfilehash: 93f8389ed3959d5747e46c1234fd8d2eae0f1ae5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359842"
---
# <a name="expression-evaluator-error-cxx0024"></a>Błąd CXX0024 programu Expression Evaluator

Operacja wymaga wartości l

Wyrażenie, które nie zostało oszacowane jako l wartością został określony dla operacji, która wymaga wartości l.

L wartością (tzw. ponieważ znajduje się po lewej stronie instrukcji przypisania) jest wyrażeniem, która odwołuje się do lokalizacji w pamięci.

Na przykład `buffer[count]` jest prawidłową wartością l, ponieważ wskazuje lokalizacji pamięci. Porównanie logiczne `zed != 0` nie jest prawidłową wartością l, ponieważ jej wartość PRAWDA lub FAŁSZ, nie daje w wyniku adres pamięci.

Ten błąd jest taka sama jak CAN0024.