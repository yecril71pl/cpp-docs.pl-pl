---
title: Błąd ewaluatora wyrażeń CXX0039 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0039
dev_langs:
- C++
helpviewer_keywords:
- CXX0039
- CAN0039
ms.assetid: 8bf698d2-e015-4595-944f-72b81aa43d22
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b5397426618c5dfcbaa6307105781ff2e6f2eb97
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048334"
---
# <a name="expression-evaluator-error-cxx0039"></a>Błąd CXX0039 programu Expression Evaluator

symbol jest niejednoznaczny

Ewaluator wyrażeń C nie można określić, które wystąpienie symboli do użycia w wyrażeniu. Symbol występuje więcej niż raz w poziomach drzewa dziedziczenia.

Należy użyć operatora rozpoznawania zakresu (`::`) Aby jawnie określić wystąpienie do użycia w wyrażeniu.

Ten błąd jest taka sama jak CAN0039.