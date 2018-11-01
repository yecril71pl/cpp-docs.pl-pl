---
title: 2.4.2 — konstrukcja sekcji
ms.date: 11/04/2016
ms.assetid: e9e6e3ea-7fc9-4925-8f68-92b8a5bb1e76
ms.openlocfilehash: 2d9fca08eecd382c9d3df60159c13ac188a1ab85
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486817"
---
# <a name="242-sections-construct"></a>2.4.2 — konstrukcja sekcji

**Sekcje** dyrektywy identyfikuje noniterative konstrukcji podziału pracy, który określa zestaw konstrukcji, które są podzielone między wątkami w zespole. Każda sekcja jest wykonywane raz przez wątek w zespole. Składnia **sekcje** dyrektywy jest następująca:

```
#pragma omp sections [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block ]
...
}
```

Klauzula jest jedną z następujących czynności:

**prywatne (** *liście zmiennych* **)**

**firstprivate (** *liście zmiennych* **)**

**lastprivate (** *liście zmiennych* **)**

**redukcja (** *operator* **:***liście zmiennych* **)**

**nowait**

Każda sekcja jest poprzedzony **sekcji** dyrektywy, mimo że **sekcji** dyrektywa jest opcjonalna w pierwszej sekcji. **Sekcji** dyrektywy musi znajdować się w obrębie zakresu leksykalne **sekcje** dyrektywy. Na końcu ma niejawne barierę **sekcje** konstruowania, chyba że **nowait** jest określony.

Ograniczenia **sekcje** dyrektywy jest następująca:

- A **sekcji** dyrektywy nie musi znajdować się poza zakres leksykalne **sekcje** dyrektywy.

- Tylko jeden **nowait** klauzula może występować na **sekcje** dyrektywy.

## <a name="cross-references"></a>Odsyłacze:

- **prywatne**, **firstprivate**, **lastprivate**, i **redukcji** zdań, zobacz [sekcji 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) na stronie 25.