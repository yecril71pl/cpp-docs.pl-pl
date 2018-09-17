---
title: __segmentlimit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __segmentlimit
dev_langs:
- C++
helpviewer_keywords:
- __segmentlimit intrinsic
- lsl instruction
ms.assetid: d0bc3630-90cb-4185-8667-686fd41e23d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e9ca899b7ad0f83faed4b8aefe318d2c62abb76
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45704993"
---
# <a name="segmentlimit"></a>__segmentlimit
**Microsoft Specific**  
  
 Generuje `lsl` instrukcji (Limit segmentów obciążenia).  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned long __segmentlimit(   
   unsigned long a   
);  
```  
  
#### <a name="parameters"></a>Parametry  
*a*<br/>
[in] Stała określająca selektor segmentu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Limit segmentów selektora segmentu, określony przez `a`pod warunkiem, że selektor jest prawidłowy i widoczne na bieżącym poziomie uprawnień.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__segmentlimit`|x86, x64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Nie można pobrać limit segmentów, ta instrukcja nie powiedzie się. W przypadku awarii ta instrukcja czyści flagę ZF i wartość zwracana jest niezdefiniowany.  
  
 Ta procedura jest dostępna wyłącznie jako wewnętrzna.  
  
## <a name="example"></a>Przykład  
  
```  
#include <stdio.h>  
  
#ifdef _M_IX86  
typedef unsigned int READETYPE;  
#else  
typedef unsigned __int64 READETYPE;  
#endif  
  
#define EFLAGS_ZF      0x00000040  
#define KGDT_R3_DATA    0x0020  
#define RPL_MASK        0x3  
  
extern "C"  
{  
unsigned long __segmentlimit (unsigned long);  
READETYPE __readeflags();  
}  
  
#pragma intrinsic(__readeflags)  
#pragma intrinsic(__segmentlimit)  
  
int main(void)  
{  
   const unsigned long initsl = 0xbaadbabe;  
   READETYPE eflags = 0;  
   unsigned long sl = initsl;  
  
   printf("Before: segment limit =0x%x eflags =0x%x\n", sl, eflags);  
   sl = __segmentlimit(KGDT_R3_DATA + RPL_MASK);  
  
   eflags = __readeflags();  
  
   printf("After: segment limit =0x%x eflags =0x%x eflags.zf = %s\n", sl, eflags, (eflags & EFLAGS_ZF) ? "set" : "clear");  
  
   // If ZF is set, the call to lsl succeeded; if ZF is clear, the call failed.  
   printf("%s\n", eflags & EFLAGS_ZF ? "Success!": "Fail!");  
  
   // You can verify the value of sl to make sure that the instruction wrote to it  
   printf("sl was %s\n", (sl == initsl) ? "unchanged" : "changed");  
  
   return 0;  
}  
```  
  
```Output  
Before: segment limit =0xbaadbabe eflags =0x0  
After: segment limit =0xffffffff eflags =0x256 eflags.zf = set  
Success!  
sl was changed  
```  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)