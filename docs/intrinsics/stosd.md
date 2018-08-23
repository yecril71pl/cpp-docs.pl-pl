---
title: __stosd | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __stosd
dev_langs:
- C++
helpviewer_keywords:
- stosd instruction
- rep stosd instruction
- __stosd intrinsic
ms.assetid: 03104247-1cea-49f6-b6f8-287917bf5680
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e63ee47c98e898fe5cba1a24078029f6afe10b15
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42464560"
---
# <a name="stosd"></a>__stosd
**Microsoft Specific**  
  
 Generuje instrukcję ciągu magazynu (`rep stosd`).  
  
## <a name="syntax"></a>Składnia  
  
```  
void __stosd(   
   unsigned long* Dest,   
   unsigned long Data,   
   size_t Count   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [out] `Dest`  
 Lokalizacja docelowa wykonać operację.  
  
 [in] `Data`  
 Dane, które mają być przechowywane.  
  
 [in] `Count`  
 Długość bloku wyrazy w liczbie mnogiej do zapisania.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__stosd`|x86, x64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Wynik jest fakt, że bitowego `Data` są zapisywane w bloku `Count` wyrazy w liczbie mnogiej w lokalizacji pamięci wskazywany przez `Dest`.  
  
 Ta procedura jest dostępna wyłącznie jako wewnętrzna.  
  
## <a name="example"></a>Przykład  
  
```  
// stosd.c  
// processor: x86, x64  
  
#include <stdio.h>  
#include <memory.h>  
#include <intrin.h>  
  
#pragma intrinsic(__stosd)  
  
int main()  
{  
    unsigned long val = 99999;  
    unsigned long a[10];  
  
    memset(a, 0, sizeof(a));  
    __stosd(a+1, val, 2);  
  
printf_s( "%u %u %u %u",  
              a[0], a[1], a[2], a[3]);   
}  
```  
  
```Output  
0 99999 99999 0  
```  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)