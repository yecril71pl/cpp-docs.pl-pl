---
title: 3.1.10 funkcja omp_get_nested | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 48736a25-5c6e-4e2d-aad0-421087663a3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7f447da6957cb385ace918120eb7ed7a5420e9f0
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686724"
---
# <a name="3110-ompgetnested-function"></a>3.1.10 Funkcja omp_get_nested
`omp_get_nested` Funkcja zwraca wartość niezerową, jeśli włączono zagnieżdżonych równoległości i 0, jeśli jest ona wyłączona. Aby uzyskać więcej informacji na zagnieżdżonych równoległości zobacz sekcję 3.1.9 na stronie 40. Format jest następujący:  
  
```  
#include <omp.h>  
int omp_get_nested(void);  
```  
  
 Jeśli implementacja nie implementuje zagnieżdżonych równoległości, ta funkcja zawsze zwraca 0.