---
title: Błąd CXX0024 programu Expression Evaluator
ms.date: 11/04/2016
f1_keywords:
- CXX0024
helpviewer_keywords:
- CXX0024
- CAN0024
ms.assetid: eca6adbd-8ff2-4f51-a1cc-a2e9d5d0a47d
ms.openlocfilehash: 525210090b0a4c2966f2e1432f85fd4bb6a8156d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195763"
---
# <a name="expression-evaluator-error-cxx0024"></a>Błąd CXX0024 programu Expression Evaluator

operacja wymaga wartości l

Wyrażenie, które nie jest szacowane do wartości l, zostało określone dla operacji wymagającej wartości l.

Wartość l-wartości (tak zwana, ponieważ pojawia się po lewej stronie instrukcji przypisania) jest wyrażeniem odwołującym się do lokalizacji pamięci.

Na przykład `buffer[count]` jest prawidłową wartością l, ponieważ wskazuje na określoną lokalizację w pamięci. Porównanie logiczne `zed != 0` nie jest prawidłową wartością l, ponieważ daje w wyniku wartość PRAWDA lub FAŁSZ, a nie na adres pamięci.

Ten błąd jest identyczny z CAN0024.
