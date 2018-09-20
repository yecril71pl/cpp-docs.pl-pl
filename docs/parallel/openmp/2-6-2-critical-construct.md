---
title: 2.6.2, konstrukcja critical | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c46ecd00-b4a2-4a5e-ba92-288c329e773a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e51bd425999081c7a06a7d5692dbea16c887fa0b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417855"
---
# <a name="262-critical-construct"></a>2.6.2 — konstrukcja krytyczna

**Krytyczne** dyrektywy identyfikuje konstrukcja, która ogranicza wykonywania skojarzone ze strukturalnego bloku do pojedynczego wątku w danym momencie. Składnia **krytyczne** dyrektywy jest następująca:

```
#pragma omp critical [(name)]  new-linestructured-block
```

Opcjonalny *nazwa* może służyć do identyfikowania krytyczne regionu. Identyfikatory używane do identyfikowania krytyczne region mają powiązania zewnętrzne i znajdują się w przestrzeni nazw, która różni się od przestrzeni nazw używanych przez etykiety, tagi, członków i zwykłymi identyfikatorami.

Wątek oczekuje się na początku krytyczne region, aż żadnego innymi wątku jest wykonywany krytyczne region (w dowolnym miejscu program) o takiej samej nazwie. Wszystkie nienazwane **krytyczne** dyrektywy mapowania tej samej nazwie nieokreślony.