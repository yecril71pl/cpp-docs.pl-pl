---
title: Błąd CXX0017 programu Expression Evaluator
ms.date: 11/04/2016
f1_keywords:
- CXX0017
helpviewer_keywords:
- CAN0017
- CXX0017
ms.assetid: af74db02-a64d-49ca-8363-3e044a107580
ms.openlocfilehash: bbf16ae9a503a8525edb42d6bf1fc4336c3f5267
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397136"
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