---
title: Wykluczanie (#import) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- exclude
dev_langs:
- C++
helpviewer_keywords:
- exclude attribute
ms.assetid: 0883248a-d4bf-420e-9848-807b28fa976e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1d553b706d4a2c21aacf23ef5ee17cca372b9c89
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="exclude-import"></a>wykluczanie (#import)
**Określonego języka C++**  
  
 Wyklucza elementów z generowaną pliki nagłówków biblioteki typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
exclude("Name1"[, "Name2",...])  
```  
  
#### <a name="parameters"></a>Parametry  
 `Name1`  
 Pierwszy element do wykluczenia.  
  
 `Name2`  
 Drugi element do wykluczenia (Jeśli to konieczne).  
  
## <a name="remarks"></a>Uwagi  
 Biblioteki typów może obejmować definicje elementów zdefiniowanych w nagłówkach systemu lub innych bibliotek typów. Ten atrybut może być dowolną liczbę argumentów, każda z nich elementu biblioteki typu najwyższego poziomu do wykluczenia.  
  
 **KOŃCOWY określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 [atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)