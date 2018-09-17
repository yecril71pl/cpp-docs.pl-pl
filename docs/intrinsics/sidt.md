---
title: __sidt | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __sidt
dev_langs:
- C++
helpviewer_keywords:
- sidt instruction
- __sidt intrinsic
ms.assetid: 01e83d14-6e63-4dea-8f64-5a0339d69641
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6731bb6a06f775c06ba16eb4885a3982d934f3cd
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45699874"
---
# <a name="sidt"></a>__sidt
**Microsoft Specific**  
  
 Przechowuje wartość rejestru Tabela deskryptora przerwania (IDTR) w określonej lokalizacji pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __sidt(  
     void *Destination);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|*miejsce docelowe*|[in] Wskaźnik do przechowywania IDTR lokalizacji w pamięci.|  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__sidt`|x86, x64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 `__sidt` Funkcji jest odpowiednikiem `SIDT` machine instrukcji. Aby uzyskać więcej informacji, Wyszukaj w dokumencie "ręcznego deweloper oprogramowania architekturze firmy Intel, wolumin 2: odwołania do zestawu instrukcji," w [Intel Corporation](https://software.intel.com/en-us/articles/intel-sdm) lokacji.  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [__lidt](../intrinsics/lidt.md)