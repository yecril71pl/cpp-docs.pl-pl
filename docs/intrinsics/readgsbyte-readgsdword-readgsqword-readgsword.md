---
title: __readgsbyte, __readgsdword, __readgsqword, __readgsword | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __readgsbyte
- __readgsdword
- __readgsqword
- __readgsword
dev_langs:
- C++
helpviewer_keywords:
- __readgsword intrinsic
- __readgsdword intrinsic
- __readgsqword intrinsic
- __readgsbyte intrinsic
ms.assetid: f822632d-854c-4558-a71b-cdfc3eea2236
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9cc4c44807a40425d4531c747526148837e0a25c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711168"
---
# <a name="readgsbyte-readgsdword-readgsqword-readgsword"></a>__readgsbyte, __readgsdword, __readgsqword, __readgsword
**Microsoft Specific**  
  
 Odczyt pamięci z lokalizacji określonej przez przesunięcie względem początku segmentu GS.  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned char __readgsbyte(   
   unsigned long Offset   
);  
unsigned short __readgsword(   
   unsigned long Offset   
);  
unsigned long __readgsdword(   
   unsigned long Offset  
);  
unsigned __int64 __readgsqword(   
   unsigned long Offset   
);  
```  
  
#### <a name="parameters"></a>Parametry  
*Przesunięcie*<br/>
[in] Przesunięcie od początku `GS` do odczytu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zawartość pamięci bajt, wyraz, podwójne słowo lub quadword (co zostało wskazane przez nazwę funkcji o nazwie) w lokalizacji `GS:[Offset]`.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__readgsbyte`|X64|  
|`__readgsdword`|X64|  
|`__readgsqword`|X64|  
|`__readgsword`|X64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Te funkcje wewnętrzne są dostępne tylko w trybie jądra i procedury są dostępne tylko jako funkcje wewnętrzne.  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [__writegsbyte, \__writegsdword, \__writegsqword, \__writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)   
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)