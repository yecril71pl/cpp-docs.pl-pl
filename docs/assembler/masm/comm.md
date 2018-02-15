---
title: COMM | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COMM
dev_langs:
- C++
helpviewer_keywords:
- COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6258a584d39f598b32c43affc0ef2569b77b2047
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="comm"></a>COMM
Tworzy zmienną gminna z atrybutów określonych w `definition`.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
COMM definition [[, definition]] ...  
```  
  
## <a name="remarks"></a>Uwagi  
 Każdy `definition` ma następujący format:  
  
 [[*langtype*]] [[**NEAR** &#124; **DALEKIEGO**]] *etykiety***:**`type`[[**:***liczba*]]  
  
 *Etykiety* to nazwa zmiennej. `type` Może być dowolnym specyfikatora typu ([BAJTÓW](../../assembler/masm/byte-masm.md), [WORD](../../assembler/masm/word.md)i tak dalej) lub liczba całkowita określająca liczbę bajtów. *Liczba* określa liczbę obiektów danych (co jest ustawieniem domyślnym).  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)