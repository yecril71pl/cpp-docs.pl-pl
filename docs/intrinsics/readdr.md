---
title: __readdr | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __readdr
dev_langs:
- C++
helpviewer_keywords:
- __readdr intrinsic
ms.assetid: 061b05da-c85e-4052-b392-106f14bb84f1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1d5cabbd1d779de4c6c081b57b8f241d9fa92f62
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709064"
---
# <a name="readdr"></a>__readdr
Odczytuje wartość rejestru określonego debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned         __readdr(unsigned int DebugRegister);  
unsigned __int64 __readdr(unsigned int DebugRegister);  
```  
  
#### <a name="parameters"></a>Parametry  
*DebugRegister*<br/>
[in] Zarejestruj stałą z zakresu od 0 do 7, który identyfikuje debugowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość rejestru określonego debugowania.  
  
## <a name="remarks"></a>Uwagi  
 Te funkcje wewnętrzne są dostępne tylko w trybie jądra, i procedury są dostępne tylko jako funkcje wewnętrzne.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__readdr`|x86, x64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [__readeflags](../intrinsics/readeflags.md)