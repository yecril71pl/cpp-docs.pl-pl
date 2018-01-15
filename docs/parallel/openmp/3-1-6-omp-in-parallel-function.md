---
title: 3.1.6 funkcja omp_in_parallel | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: db6e3a63-2a0a-4b8e-8cc6-c6b49edca5fb
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2e5d05af81eb112894ca27a7599c271138893ee1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="316-ompinparallel-function"></a>3.1.6 Funkcja omp_in_parallel
**Omp_in_parallel** funkcja zwraca wartość niezerową, jeśli jest to w zakres dynamiczny wykonywania równoległego regionu równolegle; w przeciwnym razie zwraca wartość 0. Format jest następujący:  
  
```  
#include <omp.h>  
int omp_in_parallel(void);  
```  
  
 Ta funkcja zwraca wartość niezerową, gdy jest wywoływany z w regionie wykonywane równolegle, w tym zagnieżdżonych regionów, które są serializowane.