---
title: Błąd ewaluatora wyrażeń CXX0017 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0017
dev_langs:
- C++
helpviewer_keywords:
- CAN0017
- CXX0017
ms.assetid: af74db02-a64d-49ca-8363-3e044a107580
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 431071137fb3f5b1b276327ee7d21f323ac24c5b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46136247"
---
# <a name="expression-evaluator-error-cxx0017"></a>Błąd CXX0017 programu Expression Evaluator

Nie odnaleziono symbolu

Nie można odnaleźć symboli, określonego w wyrażeniu.

Jedną z możliwych przyczyn tego błędu jest niezgodność wielkości liter w nazwie symboli. Ponieważ C i C++ jest uwzględniana wielkość liter języków, należy podać nazwę symbolu w dokładne dopasowanie wielkości liter, w którym jest zdefiniowany w źródle.

Ten błąd może wystąpić podczas próby rzutowanie typu zmiennej, aby oglądać zmiennej podczas debugowania. `typedef` Deklaruje nową nazwę typu, ale nie definiuje nowego typu. Typecast podjęto w debugerze wymaga nazwy zdefiniowanego typu.

Ten błąd jest taka sama jak CAN0017.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem, korzystając z poniższymi możliwymi rozwiązaniami

1. Sprawdź, czy symbol jest już zadeklarowany w punkcie w programie, w którym jest używany.

1. Używaj nazwą rzeczywistego typu w celu rzutowania zmiennych w debugerze, zamiast `typedef`-zdefiniowaną nazwę.