---
title: 3.1.10 funkcja omp_get_nested | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 48736a25-5c6e-4e2d-aad0-421087663a3c
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0447fd872a44d2c1eefb751e501eba4df5ec8b8f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="3110-ompgetnested-function"></a>3.1.10 Funkcja omp_get_nested
`omp_get_nested` Funkcja zwraca wartość niezerową, jeśli włączono zagnieżdżonych równoległości i 0, jeśli jest ona wyłączona. Aby uzyskać więcej informacji na zagnieżdżonych równoległości zobacz sekcję 3.1.9 na stronie 40. Format jest następujący:  
  
```  
#include <omp.h>  
int omp_get_nested(void);  
```  
  
 Jeśli implementacja nie implementuje zagnieżdżonych równoległości, ta funkcja zawsze zwraca 0.