---
title: __movsd | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __movsd
dev_langs:
- C++
helpviewer_keywords:
- rep movsd instruction
- __movsd intrinsic
- movsd instruction
ms.assetid: eb5cccf3-aa76-47f0-b9fc-eeca38fd943f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 659da66ea74088247a9eb46ae25f9920050719a1
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42466431"
---
# <a name="movsd"></a>__movsd
**Microsoft Specific**  
  
 Generuje ciąg Przenieś (`rep movsd`) instrukcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __movsd(   
   unsigned long* Dest,   
   unsigned long* Source,   
   size_t Count   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [out] `Dest`  
 Lokalizacja docelowa wykonać operację.  
  
 [in] `Source`  
 Źródło działania.  
  
 [in] `Count`  
 Liczba wyrazy w liczbie mnogiej do skopiowania.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__movsd`|x86, x64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 W wyniku pierwsze `Count` wyrazy w liczbie mnogiej wskazywany przez `Source` są kopiowane do `Dest` ciągu.  
  
 Ta procedura jest dostępna wyłącznie jako wewnętrzna.  
  
## <a name="example"></a>Przykład  
  
```  
// movsd.cpp  
// processor: x86, x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(__movsd)  
  
int main()  
{  
    unsigned long a1[10];  
    unsigned long a2[10] = {950, 850, 750, 650, 550, 450, 350,  
                            250, 150, 50};  
    __movsd(a1, a2, 10);  
  
    for (int i = 0; i < 10; i++)  
        printf_s("%d ", a1[i]);  
    printf_s("\n");  
}  
```  
  
```Output  
950 850 750 650 550 450 350 250 150 50   
```  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)