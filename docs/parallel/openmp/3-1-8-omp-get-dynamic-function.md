---
title: 3.1.8 funkcja omp_get_dynamic | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c03e2daf-29c9-49e3-9b67-b980ad1ab195
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af7755173ab884a40a5f8a41f432f265cc1e6c32
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="318-ompgetdynamic-function"></a>3.1.8 Funkcja omp_get_dynamic
**Omp_get_dynamic** funkcja zwraca wartość niezerową, jeśli dynamiczne Dostosowywanie wątków jest włączona, a w przeciwnym razie zwraca wartość 0. Format jest następujący:  
  
```  
#include <omp.h>  
int omp_get_dynamic(void);  
```  
  
 Jeśli implementacja nie implementuje dynamiczne Dostosowywanie to liczba wątków, ta funkcja zawsze zwraca wartość 0.  
  
## <a name="cross-references"></a>Odsyłacze:  
  
-   Opis korekty wątku dynamicznej, zobacz [sekcji 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stronie 39.