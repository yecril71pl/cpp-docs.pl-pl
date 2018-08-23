---
title: __debugbreak | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __debugbreak_cpp
- __debugbreak
dev_langs:
- C++
helpviewer_keywords:
- breakpoints, __debugbreak intrinsic
- __debugbreak intrinsic
ms.assetid: 1d1e1c0c-891a-4613-ae4b-d790094ba830
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 71b7dfca165e76880370368282bdbd7728315cfa
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465516"
---
# <a name="debugbreak"></a>__debugbreak
**Microsoft Specific**  
  
 Powoduje, że punkt przerwania w kodzie, gdzie użytkownik jest monitowany o uruchomienia debugera.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __debugbreak();  
```  
  
## <a name="requirements"></a>Wymagania  
  
|Wewnętrzne|Architektura|nagłówek|  
|---------------|------------------|------------|  
|`__debugbreak`|x86, ARM, x64|\<intrin.h>|  
  
## <a name="remarks"></a>Uwagi  
 `__debugbreak` Kompilatora wewnętrzne, podobnie jak [DebugBreak](http://msdn.microsoft.com/library/windows/desktop/ms679297.aspx), jest przenośny sposób Win32 i spowodować, że punkt przerwania.  
  
> [!NOTE]
>  Podczas kompilowania za pomocą **/CLR**, funkcja nadrzędnym `__debugbreak` zostaną skompilowane do MSIL. `asm int 3` powoduje, że funkcja jest kompilowana do natywnego. Aby uzyskać więcej informacji, zobacz [__asm](../assembler/inline/asm.md).  
  
 Na przykład:  
  
```  
main() {  
   __debugbreak();  
}  
```  
  
 jest podobny do:  
  
```  
main() {  
   __asm {  
      int 3  
   }  
}  
```  
  
 na x86 komputera.  
  
 Ta procedura jest dostępna wyłącznie jako wewnętrzna.  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)