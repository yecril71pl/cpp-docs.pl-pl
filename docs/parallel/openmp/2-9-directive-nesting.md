---
title: 2.9 Zagnieżdżanie dyrektywy
ms.date: 11/04/2016
ms.assetid: 6565a43c-fd2d-4366-8322-8d75e1b06600
ms.openlocfilehash: 804cafd65fde19e501b89c47925f471143d74938
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438731"
---
# <a name="29-directive-nesting"></a>2.9 Zagnieżdżanie dyrektywy

Dynamiczne zagnieżdżanie dyrektyw muszą być zgodne z następującymi zasadami:

- A **równoległe** dyrektywy dynamicznie wewnątrz innego **równoległe** logicznie ustanawia nowy zespół, który składa się z bieżącym wątkiem, chyba że zagnieżdżone równoległości jest włączona.

- **dla**, **sekcje**, i **pojedynczego** dyrektyw, które powiązania do tej samej **równoległe** nie mogą być zagnieżdżone wewnątrz siebie nawzajem.

- **krytyczne** dyrektywy o takiej samej nazwie nie mogą być zagnieżdżone wewnątrz siebie nawzajem. Należy pamiętać, że to ograniczenie nie są wystarczające do uniknięcia zakleszczenia.

- **dla**, **sekcje**, i **pojedynczego** dyrektywy nie są dozwolone w zakresie dynamiczne **krytyczne**, **uporządkowane**, i **wzorca** regionów, jeśli dyrektywy powiązania do tej samej **równoległe** jako regionów.

- **bariera** dyrektywy nie są dozwolone w zakresie dynamiczne **dla**, **uporządkowane**, **sekcje**, **pojedynczego**, **wzorca**, i **krytyczne** regionów, jeśli dyrektywy powiązania do tej samej **równoległe** jako regionów.

- **główny** dyrektywy nie są dozwolone w zakresie dynamiczne **dla**, **sekcje**, i **pojedynczego** dyrektywy Jeśli **wzorzec** dyrektywy powiązania do tej samej **równoległe** jako dyrektyw podziału pracy.

- **uporządkowane** dyrektywy nie są dozwolone w zakresie dynamiczne **krytyczne** regionów, jeśli dyrektywy powiązania do tej samej **równoległe** jako regionów.

- Wszystkie dyrektywy, które są dozwolone podczas wykonywania dynamicznie w ramach równoległego regionu również jest dozwolone, gdy wykonywane poza równoległego regionu. Po wykonaniu dynamicznie, poza regionem równolegle z określonych przez użytkownika, dyrektywa jest wykonywana przez zespół składa się z głównego wątku.