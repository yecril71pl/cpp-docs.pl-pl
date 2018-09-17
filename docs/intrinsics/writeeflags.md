---
title: __writeeflags | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __writeeflags
dev_langs:
- C++
helpviewer_keywords:
- __writeeflags intrinsics
ms.assetid: a62a522c-d7fa-4f10-a620-a3b32bdf3f17
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c01e10a77278f0a02658778ec178f0a4226eb36
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45704863"
---
# <a name="writeeflags"></a>__writeeflags
Zapisuje określoną wartość do programu, stan i kontroli (EFLAGS) rejestru.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __writeeflags(unsigned Value);  
void __writeeflags(unsigned __int64 Value);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|*Wartość*|[in] Wartość do zapisu do rejestru EFLAGS. `Value` Parametr jest 32-bitowy długa dla platform 32-bitowych i 64-bitowy na platformie 64-bitowej.|  
  
## <a name="remarks"></a>Uwagi  
 Te procedury są dostępne tylko jako funkcje wewnętrzne.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__writeeflags`|x86, x64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [__readeflags](../intrinsics/readeflags.md)