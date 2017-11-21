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
ms.openlocfilehash: ab64740cd5f04b4a707a702f0bf39174907fc8fc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [Odwołania do dyrektyw](../../assembler/masm/directives-reference.md)