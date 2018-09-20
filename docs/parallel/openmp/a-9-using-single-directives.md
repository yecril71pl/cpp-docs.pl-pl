---
title: A.9 użycie pojedynczej dyrektywy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0c0f9495-5794-4db9-883b-a12e3a9f1328
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a3a201450d54355aa96f0ea712ad9fa0f70f63f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46448093"
---
# <a name="a9---using-single-directives"></a>A.9   Użycie pojedynczej dyrektywy

W poniższym przykładzie pokazano `single` — dyrektywa ([sekcji 2.4.3](../../parallel/openmp/2-4-3-single-construct.md) na stronie 15). W przykładzie, tylko jednego wątku (zazwyczaj pierwszy wątek napotka `single` dyrektywy) wyświetla komunikat o postępie. Użytkownik musi nie należy czynić żadnych założeń jako do wątku, który będzie wykonywał `single` sekcji. Wszystkie inne wątki pozwoli na pominięcie `single` sekcji, a następnie zatrzyma barierę na końcu `single` konstruowania. Jeśli inne wątki mogą kontynuować bez oczekiwania na wykonanie wątku `single` sekcji `nowait` można określić klauzuli w `single` dyrektywy.

```
#pragma omp parallel
{
    #pragma omp single
        printf_s("Beginning work1.\n");
    work1();
    #pragma omp single
        printf_s("Finishing work1.\n");
    #pragma omp single nowait
        printf_s("Finished work1 and beginning work2.\n");
    work2();
}
```