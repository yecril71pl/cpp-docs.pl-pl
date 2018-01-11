---
title: __readcr0 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __readcr0
dev_langs: C++
helpviewer_keywords: __readcr0 intrinsic
ms.assetid: 25bdb093-d83c-48d7-9c0f-224de8e2c61c
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 66561c82d055d4763c5751dd46f7d13c2080266c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="readcr0"></a>__readcr0
**Dotyczące firmy Microsoft**  
  
 Odczytuje rejestru CR0 i zwraca jego wartość.  
  
## <a name="syntax"></a>Składnia  
  
```  
unsigned long __readcr0(void);  /* X86 */  
unsigned __int64 __readcr0(void);  /* X64 */  
  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość rejestru CR0.  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__readcr0`|x86,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
## <a name="remarks"></a>Uwagi  
 Tym wewnętrzna jest dostępna tylko w trybie jądra, a procedura jest dostępna jako funkcja wewnętrzna tylko.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)