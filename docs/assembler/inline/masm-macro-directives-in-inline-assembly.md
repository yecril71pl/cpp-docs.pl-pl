---
title: Dyrektywy makra MASM w zestawie wbudowanym | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- directives, macros
- inline assembly, macro directives
- macros, directives
- MASM (Microsoft Macro Assembler), inline assembly macro directives
ms.assetid: 83643a09-1699-40a8-8ef2-13502bc4ac2c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0df9f8584b87e511c43430a5c0df7dac61805ede
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="masm-macro-directives-in-inline-assembly"></a>Dyrektywy makra MASM w zestawie wbudowanym
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Asembler wbudowany nie jest asemblera makr. Nie można użyć dyrektywy makra MASM (**makro**, `REPT`, **IRC**, `IRP`, i `ENDM`) lub makro operatory (**<>**, **!** ,  **&** , `%`, i `.TYPE`). `__asm` Bloku można użyć dyrektywy preprocesora C, jednak. Zobacz [przy użyciu języka C lub C++ w blokach __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md) Aby uzyskać więcej informacji.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z języka Asembler w blokach __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)