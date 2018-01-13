---
title: 3.1.8 funkcja omp_get_dynamic | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: c03e2daf-29c9-49e3-9b67-b980ad1ab195
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bd4ec73b82848efcdface781738639b05a256958
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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