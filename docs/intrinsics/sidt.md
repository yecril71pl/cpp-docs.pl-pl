---
title: __sidt | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __sidt
dev_langs:
- C++
helpviewer_keywords:
- sidt instruction
- __sidt intrinsic
ms.assetid: 01e83d14-6e63-4dea-8f64-5a0339d69641
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0d28973552e8477f5a9662035b540fb8a75984c9
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="sidt"></a>__sidt
**Microsoft Specific**  
  
 Przechowuje wartość rejestru tabeli deskryptora przerwań (IDTR) w lokalizacji określonej pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __sidt(  
     void *Destination);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] `Destination`|Wskaźnik do przechowywania IDTR lokalizacji w pamięci.|  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__sidt`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 `__sidt` Funkcji jest odpowiednikiem `SIDT` maszyny instrukcji. Aby uzyskać więcej informacji, Wyszukaj w dokumencie "ręcznego deweloper oprogramowania architekturze firmy Intel, wolumin 2: Odwołanie zestaw instrukcji," w [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) lokacji.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [__lidt](../intrinsics/lidt.md)