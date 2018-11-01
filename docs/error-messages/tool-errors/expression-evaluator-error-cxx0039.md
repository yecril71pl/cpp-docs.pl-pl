---
title: Błąd CXX0039 programu Expression Evaluator
ms.date: 11/04/2016
f1_keywords:
- CXX0039
helpviewer_keywords:
- CXX0039
- CAN0039
ms.assetid: 8bf698d2-e015-4595-944f-72b81aa43d22
ms.openlocfilehash: 053e57a21f0cb75cbd96732edb6812b3557bcd50
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463274"
---
# <a name="expression-evaluator-error-cxx0039"></a>Błąd CXX0039 programu Expression Evaluator

symbol jest niejednoznaczny

Ewaluator wyrażeń C nie można określić, które wystąpienie symboli do użycia w wyrażeniu. Symbol występuje więcej niż raz w poziomach drzewa dziedziczenia.

Należy użyć operatora rozpoznawania zakresu (`::`) Aby jawnie określić wystąpienie do użycia w wyrażeniu.

Ten błąd jest taka sama jak CAN0039.