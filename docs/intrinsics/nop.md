---
title: __nop | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __nop
dev_langs: C++
helpviewer_keywords:
- nop instruction
- __nop intrinsic
ms.assetid: 7a2a938b-87e0-476d-a348-03ea7635b6b9
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: eef05150aab36abc6f6be76785284d017cf204ac
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="nop"></a>__nop
**Dotyczące firmy Microsoft**  
  
 Generuje kod maszynowy specyficzne dla platformy, który wykonuje żadnych operacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __nop();  
```  
  
## <a name="requirements"></a>Wymagania  
  
|— Wewnętrzne|Architektura|  
|---------------|------------------|  
|`__nop`|x86,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Plik nagłówka** \<intrin.h >  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="remarks"></a>Uwagi  
 `__nop` Funkcji jest odpowiednikiem `NOP` maszyny instrukcji. Aby uzyskać więcej informacji, Wyszukaj w dokumencie "ręcznego deweloper oprogramowania architekturze firmy Intel, wolumin 2: Odwołanie zestaw instrukcji," w [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) lokacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)   
 [__noop](../intrinsics/noop.md)