---
title: 3.1.6 funkcja omp_in_parallel | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: db6e3a63-2a0a-4b8e-8cc6-c6b49edca5fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 22b491695d2ae49336d7d8998af64e724f344d87
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="316-ompinparallel-function"></a>3.1.6 Funkcja omp_in_parallel
**Omp_in_parallel** funkcja zwraca wartość niezerową, jeśli jest to w zakres dynamiczny wykonywania równoległego regionu równolegle; w przeciwnym razie zwraca wartość 0. Format jest następujący:  
  
```  
#include <omp.h>  
int omp_in_parallel(void);  
```  
  
 Ta funkcja zwraca wartość niezerową, gdy jest wywoływany z w regionie wykonywane równolegle, w tym zagnieżdżonych regionów, które są serializowane.