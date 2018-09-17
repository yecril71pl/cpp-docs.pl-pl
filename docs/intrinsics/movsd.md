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
ms.openlocfilehash: 90b96181dc3d48edbe6f58923e62d4fd1259f3c0
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723934"
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
*docelowy*<br/>
[out] Lokalizacja docelowa wykonać operację.  
  
*Źródło*<br/>
[in] Źródło działania.  
  
*Liczba*<br/>
[in] Liczba wyrazy w liczbie mnogiej do skopiowania.  
  
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