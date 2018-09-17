---
title: __stosw | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __stosw
dev_langs:
- C++
helpviewer_keywords:
- stosw instruction
- __stosw intrinsic
- rep stosw instruction
ms.assetid: 7620fd1d-dba5-40e3-8e07-01aa68895133
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cf0e6157f184cb91605d9da8bcaea0c22806f03c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705166"
---
# <a name="stosw"></a>__stosw
**Microsoft Specific**  
  
 Generuje instrukcję ciągu magazynu (`rep stosw`).  
  
## <a name="syntax"></a>Składnia  
  
```  
void __stosw(   
   unsigned short* Dest,   
   unsigned short Data,   
   size_t Count   
);  
```  
  
#### <a name="parameters"></a>Parametry  
*docelowy*<br/>
[out] Lokalizacja docelowa wykonać operację.  
  
*Dane*<br/>
[in] Dane, które mają być przechowywane.  
  
*Liczba*<br/>
[in] Długość bloku słowa do zapisu.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__stosw`|x86, x64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Wynik jest to, że wyraz `Data` są zapisywane w bloku `Count` wyrazów w `Dest` ciągu.  
  
 Ta procedura jest dostępna wyłącznie jako wewnętrzna.  
  
## <a name="example"></a>Przykład  
  
```  
// stosw.c  
// processor: x86, x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(__stosw)  
  
int main()  
{  
    unsigned short val = 128;  
    unsigned short a[100];  
    memset(a, 0, sizeof(a));  
    __stosw(a+10, val, 2);  
    printf_s("%u %u %u %u", a[9], a[10], a[11], a[12]);     
}  
```  
  
```Output  
0 128 128 0  
```  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)