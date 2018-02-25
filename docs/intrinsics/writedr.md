---
title: __writedr | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __writedr
dev_langs:
- C++
helpviewer_keywords:
- __writedr intrinsic
ms.assetid: ac55c1ee-df2f-41d4-a429-6f369d2a934d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 57f8e72bd8472ee88db3335a968e4a9ec6fb3998
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
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
 Liczba z przedziału od 0 do 7, który identyfikuje debugowania zarejestrować.  
  
 [in] `DebugValue`  
 Zarejestruj wartość do zapisania do debugowania.  
  
## <a name="remarks"></a>Uwagi  
 Te funkcje wewnętrzne są dostępne tylko w trybie jądra, i procedury są dostępne tylko jako funkcje wewnętrzne.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__writedr`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [__readdr](../intrinsics/readdr.md)