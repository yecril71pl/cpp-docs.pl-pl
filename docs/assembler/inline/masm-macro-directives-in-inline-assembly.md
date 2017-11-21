---
title: Dyrektywy makra MASM w zestawie wbudowanym | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- directives, macros
- inline assembly, macro directives
- macros, directives
- MASM (Microsoft Macro Assembler), inline assembly macro directives
ms.assetid: 83643a09-1699-40a8-8ef2-13502bc4ac2c
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f789df759729deb3c2b548efb008ae9a27357ab2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="masm-macro-directives-in-inline-assembly"></a>Dyrektywy makra MASM w zestawie wbudowanym
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Asembler wbudowany nie jest asemblera makr. Nie można użyć dyrektywy makra MASM (**makro**, `REPT`, **IRC**, `IRP`, i `ENDM`) lub makro operatory (**<>**, **!** ,  **&** , `%`, i `.TYPE`). `__asm` Bloku można użyć dyrektywy preprocesora C, jednak. Zobacz [przy użyciu języka C lub C++ w blokach __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md) Aby uzyskać więcej informacji.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z języka asembler w blokach __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)