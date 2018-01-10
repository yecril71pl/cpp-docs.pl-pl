---
title: __svm_stgi | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __svm_stgi
dev_langs: C++
helpviewer_keywords:
- __svm_stgi intrinsic
- STGI instruction
ms.assetid: 96488da4-5587-4e99-8674-627a9e51be84
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 94e386827ae747fb3289354ba380d390756359ff
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="svmstgi"></a>__svm_stgi
**Dotyczące firmy Microsoft**  
  
 Ustawia flagę globalne przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __svm_stgi(void);  
```  
  
## <a name="remarks"></a>Uwagi  
 `__svm_stgi` Funkcji jest odpowiednikiem `STGI` maszyny instrukcji. Flagi globalne przerwań określa, czy procesor ignoruje, odłoży czy obsługuje przerwania z powodu zdarzenia, takie jak zakończenia We/Wy, alert temperatury sprzętu lub wyjątek do debugowania.  
  
 Ta funkcja obsługuje interakcji z hosta maszyny wirtualnej monitor Gość operacyjnego i jego zastosowań. Aby uzyskać więcej informacji, wyszukaj dokumentu, "wolumin ręczne AMD64 architektura programisty 2: programowania w języku systemu," numer 24593, poprawki 3.11, dokumentu w [AMD corporation](http://go.microsoft.com/fwlink/p/?linkid=23746) lokacji.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__svm_stgi`|x86,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [__svm_clgi](../intrinsics/svm-clgi.md)