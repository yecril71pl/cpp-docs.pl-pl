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
ms.openlocfilehash: b72351095fd56ae6543c2ca742983eef315f2158
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="316-ompinparallel-function"></a>3.1.6 Funkcja omp_in_parallel
**Omp_in_parallel** funkcja zwraca wartość niezerową, jeśli jest to w zakres dynamiczny wykonywania równoległego regionu równolegle; w przeciwnym razie zwraca wartość 0. Format jest następujący:  
  
```  
#include <omp.h>  
int omp_in_parallel(void);  
```  
  
 Ta funkcja zwraca wartość niezerową, gdy jest wywoływany z w regionie wykonywane równolegle, w tym zagnieżdżonych regionów, które są serializowane.