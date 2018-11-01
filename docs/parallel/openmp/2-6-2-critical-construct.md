---
title: 2.6.2 — konstrukcja krytyczna
ms.date: 11/04/2016
ms.assetid: c46ecd00-b4a2-4a5e-ba92-288c329e773a
ms.openlocfilehash: dcc0e6144be5daee2a225cda621db818e5a38e2c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539077"
---
# <a name="262-critical-construct"></a>2.6.2 — konstrukcja krytyczna

**Krytyczne** dyrektywy identyfikuje konstrukcja, która ogranicza wykonywania skojarzone ze strukturalnego bloku do pojedynczego wątku w danym momencie. Składnia **krytyczne** dyrektywy jest następująca:

```
#pragma omp critical [(name)]  new-linestructured-block
```

Opcjonalny *nazwa* może służyć do identyfikowania krytyczne regionu. Identyfikatory używane do identyfikowania krytyczne region mają powiązania zewnętrzne i znajdują się w przestrzeni nazw, która różni się od przestrzeni nazw używanych przez etykiety, tagi, członków i zwykłymi identyfikatorami.

Wątek oczekuje się na początku krytyczne region, aż żadnego innymi wątku jest wykonywany krytyczne region (w dowolnym miejscu program) o takiej samej nazwie. Wszystkie nienazwane **krytyczne** dyrektywy mapowania tej samej nazwie nieokreślony.