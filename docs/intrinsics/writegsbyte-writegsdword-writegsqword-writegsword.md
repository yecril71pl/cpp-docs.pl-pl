---
title: __writegsbyte, __writegsdword, __writegsqword, __writegsword | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __writegsbyte
- __writegsqword
- __writegsdword
- __writegsword
dev_langs:
- C++
helpviewer_keywords:
- __writegsqword intrinsic
- __writegsbyte intrinsic
- __writegsword intrinsic
- __writegsdword intrinsic
ms.assetid: 7746cf6d-2259-4139-9aab-c07dd75c8037
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5ae6f47009600c87cb260246fca474592a5e9c6
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42464746"
---
# <a name="writegsbyte-writegsdword-writegsqword-writegsword"></a>__writegsbyte, __writegsdword, __writegsqword, __writegsword
**Microsoft Specific**  
  
 Napisz pamięci w lokalizacji określonej przez przesunięcie względem początku segmentu GS.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __writegsbyte(   
   unsigned long Offset,   
   unsigned char Data   
);  
void __writegsword(   
   unsigned long Offset,   
   unsigned short Data   
);  
void __writegsdword(   
   unsigned long Offset,   
   unsigned long Data   
);  
void __writegsqword(   
   unsigned long Offset,   
   unsigned __int64 Data   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `Offset`  
 Przesunięcie od początku GS do zapisu.  
  
 [in] `Data`  
 Wartość do zapisu.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__writegsbyte`|X64|  
|`__writegsdword`|X64|  
|`__writegsqword`|X64|  
|`__writegsword`|X64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Te funkcje wewnętrzne są dostępne tylko w trybie jądra, a te procedury są dostępne tylko jako funkcje wewnętrzne.  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [__readgsbyte, \__readgsdword, \__readgsqword, \__readgsword](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)   
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)