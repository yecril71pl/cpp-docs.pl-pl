---
title: __svm_clgi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __svm_clgi
dev_langs:
- C++
helpviewer_keywords:
- CLGI instruction
- __svm_clgi intrinsic
ms.assetid: 6640f5ab-9472-46f9-a042-e15c4f1ff858
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 54f1a88acef3f3f79a39a8dd68e1beb079f30fec
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465620"
---
# <a name="svmclgi"></a>__svm_clgi
**Microsoft Specific**  
  
 Czyści flagę globalnego przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __svm_clgi( void );  
```  
  
## <a name="remarks"></a>Uwagi  
 `__svm_clgi` Funkcji jest odpowiednikiem `CLGI` machine instrukcji. Flagi globalnej przerwania określa, czy procesor ignoruje, odłoży czy obsługi przerwań z powodu zdarzenia, takie jak ukończenia operacji We/Wy, alert temperatury sprzętu lub wyjątek debugowania.  
  
 Ta funkcja obsługuje interakcji monitor maszyny wirtualnej hosta z gościa operacyjnego i jego aplikacji. Aby uzyskać więcej informacji, wyszukaj dokumentu, "AMD64 architektury programisty ręczne woluminie 2: programowania systemu" numer 24593, wersji 3.11, dokumentu w [AMD corporation](http://go.microsoft.com/fwlink/p/?linkid=23746) lokacji.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__svm_clgi`|x86, x64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [__svm_stgi](../intrinsics/svm-stgi.md)