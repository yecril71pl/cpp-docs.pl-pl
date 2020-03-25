---
title: Błąd CXX0039 programu Expression Evaluator
ms.date: 11/04/2016
f1_keywords:
- CXX0039
helpviewer_keywords:
- CXX0039
- CAN0039
ms.assetid: 8bf698d2-e015-4595-944f-72b81aa43d22
ms.openlocfilehash: 5706d002eb3d566d05b059cb04b6b1626fdb3d33
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185129"
---
# <a name="expression-evaluator-error-cxx0039"></a>Błąd CXX0039 programu Expression Evaluator

symbol jest niejednoznaczny

Ewaluatora wyrażeń języka C nie może określić, które wystąpienie symbolu ma być używane w wyrażeniu. Symbol występuje więcej niż jeden raz w drzewie dziedziczenia.

Musisz użyć operatora rozpoznawania zakresu (`::`), aby jawnie określić wystąpienie do użycia w wyrażeniu.

Ten błąd jest identyczny z CAN0039.
