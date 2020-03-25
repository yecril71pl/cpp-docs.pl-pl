---
title: Błąd CXX0017 programu Expression Evaluator
ms.date: 11/04/2016
f1_keywords:
- CXX0017
helpviewer_keywords:
- CAN0017
- CXX0017
ms.assetid: af74db02-a64d-49ca-8363-3e044a107580
ms.openlocfilehash: 64ebce0161d67c298d55095f6bc409820120c34a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196017"
---
# <a name="expression-evaluator-error-cxx0017"></a>Błąd CXX0017 programu Expression Evaluator

nie znaleziono symbolu

Nie można znaleźć symbolu określonego w wyrażeniu.

Jedną z możliwych przyczyn tego błędu jest niezgodność wielkości liter w nazwie symbolu. Ponieważ język C C++ i jest rozróżniana wielkość liter, nazwa symbolu musi być określona w dokładnie takim przypadku, w którym jest zdefiniowana w źródle.

Ten błąd może wystąpić podczas próby rzutowanie zmiennej w celu obejrzenia zmiennej podczas debugowania. `typedef` deklaruje nową nazwę dla typu, ale nie definiuje nowego typu. Rzutowaniea próba w debugerze wymaga nazwy zdefiniowanego typu.

Ten błąd jest identyczny z CAN0017.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać ten problem, można użyć następujących rozwiązań

1. Upewnij się, że symbol jest już zadeklarowany w punkcie w programie, w którym jest używany.

1. Użyj rzeczywistej nazwy typu do rzutowania zmiennych w debugerze, a nie nazwy zdefiniowanej przez `typedef`.
