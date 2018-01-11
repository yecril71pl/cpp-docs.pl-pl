---
title: __debugbreak | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- __debugbreak_cpp
- __debugbreak
dev_langs: C++
helpviewer_keywords:
- breakpoints, __debugbreak intrinsic
- __debugbreak intrinsic
ms.assetid: 1d1e1c0c-891a-4613-ae4b-d790094ba830
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 07cac11754a8b5f242c38d5fd45d4c7f0707d69a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="debugbreak"></a>__debugbreak
**Dotyczące firmy Microsoft**  
  
 Powoduje, że punkt przerwania w kodzie, gdy użytkownik otrzyma monit Uruchom debuger.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __debugbreak();  
```  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|nagłówek|  
|---------------|------------------|------------|  
|`__debugbreak`|x86, ARM,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h >|  
  
## <a name="remarks"></a>Uwagi  
 `__debugbreak` Kompilatora wewnętrzne, podobnie jak [debugbreak —](http://msdn.microsoft.com/library/windows/desktop/ms679297.aspx), to spowodować, że punkt przerwania przenośne sposób Win32.  
  
> [!NOTE]
>  Podczas kompilowania za pomocą **/CLR**, funkcja zawierająca `__debugbreak` zostaną skompilowane do MSIL. `asm int 3`powoduje, że funkcja zestawiane na natywny. Aby uzyskać więcej informacji, zobacz [__asm](../assembler/inline/asm.md).  
  
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
  
 Ta procedura jest dostępna tylko wewnętrznie.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)