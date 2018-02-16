---
title: OPCJA (MASM) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- option
dev_langs:
- C++
helpviewer_keywords:
- OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2d8e8049ecea3775b9df85eb1d5c8ee5e94a9243
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
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
|**NOM510**|**NOKEYWORD**|**NOSIGNEXTEND**|**OFFSET**|  
|**OLDMACROS**|**NOOLDMACROS**|**OLDSTRUCTS**|**NOOLDSTRUCTS**|  
|**PROC**|**PROLOGU**|**TYLKO DO ODCZYTU**|**NOREADONLY**|  
|**ZAKRES**|**NOSCOPED**|**SEGMENT**|**SETIF2**.|  
  
 Składnia języka jest **opcji języka: *** x*, gdzie *x* jest jednym z C, SYSCALL, STDCALL, PASCAL, FORTRAN lub BASIC.  SYSCALL, PASCAL FORTRAN i BASIC nie są obsługiwane z używane z [. MODEL](../../assembler/masm/dot-model.md) PŁASKIM.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)