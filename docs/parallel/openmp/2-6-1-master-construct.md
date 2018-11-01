---
title: 2.6.1 — konstrukcja główna
ms.date: 11/04/2016
ms.assetid: c092064b-ea57-4d4e-9c99-a004d65656fe
ms.openlocfilehash: 0501b1fdfbd36829cee2793fc0f7bb03daeda900
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475533"
---
# <a name="261-master-construct"></a>2.6.1 — konstrukcja główna

**Wzorca** dyrektywy identyfikuje konstrukcja, która określa ze strukturą blok, który jest wykonywany przez główny wątek zespołu. Składnia **wzorca** dyrektywy jest następująca:

```
#pragma omp master new-linestructured-block
```

Inne wątki w zespole nie wykonuj skojarzone ze strukturalnego bloku. Bez problemu dorozumianych na wpis do lub wyjście z konstrukcja master nie istnieje.