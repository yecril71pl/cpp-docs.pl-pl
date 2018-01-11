---
title: __writemsr | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __writemsr
dev_langs: C++
helpviewer_keywords:
- Write Model Specific Register instruction
- wrmsr instruction
- __writemsr intrinsic
ms.assetid: 938b1553-51a8-4822-a818-6bed79b0fde5
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9a4b60fcc303afcb0c645561009279dd9fced8db
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="writemsr"></a>__writemsr
**Dotyczące firmy Microsoft**  
  
 Generuje zapisu można zarejestrować określonego modelu (`wrmsr`) instrukcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __writemsr(   
   unsigned long Register,   
   unsigned __int64 Value   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`Register`  
 Rejestr określonego modelu.  
  
 [in]`Value`  
 Wartość do zapisu.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__writemsr`|x86,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja może być używana tylko w trybie jądra, a ta procedura jest dostępna jako funkcja wewnętrzna tylko.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)