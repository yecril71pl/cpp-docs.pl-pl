---
title: __svm_invlpga | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __svm_invlpga
dev_langs:
- C++
helpviewer_keywords:
- __svm_invlpga intrinsic
- INVLPGA instruction
ms.assetid: aa6578ce-8278-464b-8815-a0fc45330915
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c2f962ec4a348cca7ffdf43852cb01d673f3fb18
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706605"
---
# <a name="svminvlpga"></a>__svm_invlpga
**Microsoft Specific**  
  
 Unieważnienie wpisu mapowania adresu w buforze aside wygląd tłumaczenia tego komputera. Parametry określają wirtualny adres i adresu miejsca identyfikator strony do unieważnienia.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __svm_invlpga(  
     void *Va,  
     int ASID);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|*oceny luk w zabezpieczeniach*|[in] Wirtualny adres strony do unieważnienia.|  
|*ASID*|[in] Adres miejsca identyfikator (ASID) strony do unieważnienia.|  
  
## <a name="remarks"></a>Uwagi  
 `__svm_invlpga` Funkcji jest odpowiednikiem `INVLPGA` machine instrukcji. Ta funkcja obsługuje interakcji monitor maszyny wirtualnej hosta z gościa operacyjnego i jego aplikacji. Aby uzyskać więcej informacji, wyszukaj dokumentu, "AMD64 architektury programisty ręczne woluminie 2: programowania systemu" numer 24593, wersji 3.11, dokumentu w [AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/) lokacji.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__svm_invlpga`|x86, x64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)