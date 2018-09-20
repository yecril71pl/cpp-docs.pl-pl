---
title: 2.9 zagnieżdżanie dyrektywy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 6565a43c-fd2d-4366-8322-8d75e1b06600
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b9558180a2f063171be563219f89ec3858e37a5d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396992"
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