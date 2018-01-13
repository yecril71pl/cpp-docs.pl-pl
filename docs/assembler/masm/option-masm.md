---
title: OPCJA (MASM) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: option
dev_langs: C++
helpviewer_keywords: OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f449606b143bfbf188e878b261f3d35017846862
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="option-masm"></a>OPTION (MASM)
Włącza i wyłącza funkcje asemblera.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
OPTION   
optionlist  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Dostępne opcje to:  
  
|||||  
|-|-|-|-|  
|**CASEMAP**|**DOTNAME**|**NODOTNAME**|**EMULATOR**|  
|**NOEMULATOR**|**EPILOGU**|**EXPR16**|**EXPR32**|  
|**JĘZYK**|**LJMP**|**NOLJMP**|**M510**|  
|**NOM510**|**NOKEYWORD**|**NOSIGNEXTEND**|**PRZESUNIĘCIE**|  
|**OLDMACROS**|**NOOLDMACROS**|**OLDSTRUCTS**|**NOOLDSTRUCTS**|  
|**PROC**|**PROLOGU**|**TYLKO DO ODCZYTU**|**NOREADONLY**|  
|**ZAKRES**|**NOSCOPED**|**SEGMENT**|**SETIF2**.|  
  
 Składnia języka jest **opcji języka:***x*, gdzie *x* jest jednym z C, SYSCALL, STDCALL, PASCAL, FORTRAN lub BASIC.  SYSCALL, PASCAL FORTRAN i BASIC nie są obsługiwane z używane z [. MODEL](../../assembler/masm/dot-model.md) PŁASKIM.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)