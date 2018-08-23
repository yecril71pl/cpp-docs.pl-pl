---
title: __writedr | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __writedr
dev_langs:
- C++
helpviewer_keywords:
- __writedr intrinsic
ms.assetid: ac55c1ee-df2f-41d4-a429-6f369d2a934d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 598b95df8fd2f4dd2826fcfa1f59a7e2daa8d523
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465352"
---
# <a name="writedr"></a>__writedr
Zapisuje określoną wartość do rejestru określonego debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __writedr(unsigned DebugRegister, unsigned DebugValue);  
void __writedr(unsigned DebugRegister, unsigned __int64 DebugValue);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `DebugRegister`  
 Liczba z przedziału od 0 do 7, który identyfikuje debugowania rejestru.  
  
 [in] `DebugValue`  
 Zarejestruj wartość do zapisania do debugowania.  
  
## <a name="remarks"></a>Uwagi  
 Te funkcje wewnętrzne są dostępne tylko w trybie jądra, i procedury są dostępne tylko jako funkcje wewnętrzne.  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__writedr`|x86, x64|  
  
 **Plik nagłówkowy** \<intrin.h >  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [__readdr](../intrinsics/readdr.md)