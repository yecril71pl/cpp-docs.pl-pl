---
title: 2.4.3 Pojedyncza konstrukcja
ms.date: 11/04/2016
ms.assetid: 15c180cd-e462-4b41-bf8c-cb8b1afb1a9b
ms.openlocfilehash: 7dda98ee83ee08adc29830a9c4ada71a208705fe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466368"
---
# <a name="243-single-construct"></a>2.4.3 Pojedyncza konstrukcja

**Pojedynczego** dyrektywy identyfikuje konstrukcja, która określa, czy skojarzony ze strukturalnego bloku jest wykonywana przez tylko jeden wątek w zespole (niekoniecznie głównego wątku). Składnia **pojedynczego** dyrektywy jest następująca:

```
#pragma omp single [clause[[,] clause] ...] new-linestructured-block
```

Klauzula jest jedną z następujących czynności:

**prywatne (** *liście zmiennych* **)**

**firstprivate (** *liście zmiennych* **)**

**copyprivate (** *liście zmiennych* **)**

**nowait**

Niejawne problemu po **pojedynczego** konstruowania, chyba że **nowait** jest określona klauzula.

Ograniczenia **pojedynczego** dyrektywy jest następująca:

- Tylko jeden **nowait** klauzula może występować na **pojedynczego** dyrektywy.

- **Copyprivate** nie można używać klauzuli z **nowait** klauzuli.

## <a name="cross-references"></a>Odsyłacze:

- **prywatne**, **firstprivate**, i **copyprivate** zdań, zobacz [sekcji 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) na stronie 25.