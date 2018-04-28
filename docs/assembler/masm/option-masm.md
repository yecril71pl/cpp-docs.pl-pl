---
title: OPCJA (MASM) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- option
dev_langs:
- C++
helpviewer_keywords:
- OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 80291c805cad3ef041fffc58983ff399da07c9d9
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
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
  
 Składnia języka jest **opcji języka: *** x*, gdzie *x* jest jednym z C, SYSCALL, STDCALL, PASCAL, FORTRAN lub BASIC.  SYSCALL, PASCAL FORTRAN i BASIC nie są obsługiwane z używane z [. MODEL](../../assembler/masm/dot-model.md) PŁASKIM.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)