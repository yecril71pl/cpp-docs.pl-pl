---
title: _mm_stream_si64x | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _mm_stream_si64x
dev_langs: C++
helpviewer_keywords:
- movnti instruction
- _mm_stream_si64x intrinsic
ms.assetid: 114c2cd0-085f-41aa-846e-87bdd56c9ee7
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 00d3420fc070eaaecfd368ef27a33915f3dbfa2c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="mmstreamsi64x"></a>_mm_stream_si64x  
  
**Dotyczące firmy Microsoft**  
  
 Generuje instrukcje MOVNTI. Zapisuje dane `Source` w lokalizacji pamięci, określony przez `Dest`, bez zanieczyszczenie pamięci podręcznych.  
  
## <a name="syntax"></a>Składnia  
  
```  
void _mm_stream_si64x(   
   __int64 * Dest,   
   __int64 Source   
);  
```  
  
#### <a name="parameters"></a>Parametry  
  
 [out]`Dest`  
 Wskaźnik do lokalizację do zapisania danych źródłowych w celu.  
  
 [in]`Source`  
 Dane do zapisania.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`_mm_stream_si64x`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
  
 Ta procedura jest dostępna tylko wewnętrznie.  
  
## <a name="example"></a>Przykład  
  
```C  
// _mm_stream_si64x.c  
// processor: x64  
  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(_mm_stream_si64x)  
  
int main()  
{  
    __int64 val = 0xFFFFFFFFFFFFI64;  
    __int64 a[10];  
  
    memset(a, 0, sizeof(a));  
    _mm_stream_si64x(a+1, val);  
    printf_s( "%I64x %I64x %I64x %I64x", a[0], a[1], a[2], a[3]);   
}  
```  
  
```Output  
0 ffffffffffff 0 0  
```  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)