---
title: 2.4.2 konstrukcja sections | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e9e6e3ea-7fc9-4925-8f68-92b8a5bb1e76
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 35ae940e37b40cbb9c883c4d7d6bca7b0fa65520
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410551"
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