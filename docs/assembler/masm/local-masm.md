---
title: LOKALNE (MASM) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Local
dev_langs: C++
helpviewer_keywords: LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 45ee0a98d614ee10cb7393c0e616459526b37531
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="local-masm"></a>LOCAL (MASM)
W pierwszej dyrektywy wewnątrz makr **lokalnego** definiuje etykiety, które są unikatowe dla każdego wystąpienia makra.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      LOCAL localname [[, localname]]...  
LOCAL label [[ [count ] ]] [[:type]] [[, label [[ [count] ]] [[type]]]]...  
```  
  
## <a name="remarks"></a>Uwagi  
 W drugiej dyrektywy w ramach definicji procedury (**PROC**), **lokalnego** tworzy opartego na stosie zmienne, które istnieją w czasie trwania procedury. *Etykiety* może być prostej zmiennej lub tablica zawierająca *liczba* elementów.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)