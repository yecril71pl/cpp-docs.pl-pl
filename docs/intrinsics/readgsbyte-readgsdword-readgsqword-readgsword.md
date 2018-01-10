---
title: __readgsbyte, __readgsdword, __readgsqword, __readgsword | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- __readgsbyte
- __readgsdword
- __readgsqword
- __readgsword
dev_langs: C++
helpviewer_keywords:
- __readgsword intrinsic
- __readgsdword intrinsic
- __readgsqword intrinsic
- __readgsbyte intrinsic
ms.assetid: f822632d-854c-4558-a71b-cdfc3eea2236
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b8eb0cd893553e16bea326e4ccb81c2602fe352b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="readgsbyte-readgsdword-readgsqword-readgsword"></a>__readgsbyte, __readgsdword, __readgsqword, __readgsword
**Dotyczące firmy Microsoft**  
  
 Odczytać pamięci z lokalizacji określonej przez przesunięcie względem początku GS segmentu.  
  
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
 [in]`Offset`  
 Przesunięcie od początku `GS` do odczytu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zawartość pamięci bajt, word, wyraz o podwójnej precyzji lub quadword (wskazywanego przez nazwę funkcji o nazwie) w lokalizacji `GS:[Offset]`.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__readgsbyte`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__readgsdword`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__readgsqword`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__readgsword`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Te funkcje wewnętrzne są dostępne tylko w trybie jądra, i procedury są dostępne tylko jako funkcje wewnętrzne.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [__writegsbyte, \__writegsdword, \__writegsqword, \__writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)   
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)