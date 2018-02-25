---
title: __movsq | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __movsq
dev_langs:
- C++
helpviewer_keywords:
- __movsq intrinsic
- rep movsq instruction
- movsq instruction
ms.assetid: be116a6e-2176-4ca4-93b1-9ccf3e7e7835
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ba5a5099d37e3446e74d168d006ace149d78c73d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="movsq"></a>__movsq
**Microsoft Specific**  
  
 Generuje powtarzania ciągu Przenieś (`rep movsq`) instrukcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __movsq(   
   unsigned char* Dest,   
   unsigned char* Source,   
   size_t Count   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [out] `Dest`  
 Miejsce docelowe operacji.  
  
 [in] `Source`  
 Źródło operacji.  
  
 [in] `Count`  
 Liczba quadwords do skopiowania.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__movsq`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 W wyniku pierwszy `Count` quadwords wskazywana przez `Source` są kopiowane do `Dest` ciągu.  
  
 Ta procedura jest dostępna tylko wewnętrznie.  
  
## <a name="example"></a>Przykład  
  
```  
// movsq.cpp  
// processor: x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(__movsq)  
  
int main()  
{  
    unsigned __int64 a1[10];  
    unsigned __int64 a2[10] = {950, 850, 750, 650, 550, 450, 350, 250,  
                               150, 50};  
    __movsq(a1, a2, 10);  
  
    for (int i = 0; i < 10; i++)  
       printf_s("%d ", a1[i]);  
    printf_s("\n");  
}  
```  
  
```Output  
950 850 750 650 550 450 350 250 150 50   
```  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)