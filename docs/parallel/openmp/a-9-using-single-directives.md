---
title: Pojedynczy dyrektywy Using A.9 | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: bc0e0e08b0b7bdea05bf4c627ae33cc42298c6dc
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="a9---using-single-directives"></a>A.9   Użycie pojedynczej dyrektywy
W poniższym przykładzie pokazano `single` — dyrektywa ([sekcji 2.4.3](../../parallel/openmp/2-4-3-single-construct.md) na stronie 15). W tym przykładzie, tylko jeden wątek (zazwyczaj pierwszy wątek napotka `single` dyrektywy) wyświetla komunikat o postępie. Użytkownik nie należy żadnym założeniu jako do wątku, który zostanie wykonany `single` sekcji. Inne wątki pominie `single` sekcji i zatrzyma się w bariery na końcu `single` utworzenia. Jeśli inne wątki przejść bez oczekiwania na wykonanie wątku `single` sekcji `nowait` można określić klauzuli `single` dyrektywy.  
  
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