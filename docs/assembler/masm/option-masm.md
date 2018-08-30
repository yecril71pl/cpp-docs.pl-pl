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
ms.openlocfilehash: 4a2dcbc55d6a2d033cde3b6189618afd67bdc3fb
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43221512"
---
# <a name="option-masm"></a>OPTION (MASM)
Włącza i wyłącza funkcje asembler.  
  
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
|**O OKREŚLONYM ZAKRESIE**|**NOSCOPED**|**SEGMENT**|**SETIF2**.|  
  
 Składnia języka jest **opcji języka:**<em>x</em>, gdzie *x* jest jednym z C, SYSCALL, STDCALL, PASCAL, PASCAL lub BASIC.  SYSCALL, PASCAL, PASCAL i BASIC są nieobsługiwane w przypadku używany z [. MODEL](../../assembler/masm/dot-model.md) PROSTEGO.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)