---
title: Dyrektywy makra MASM w zestawie wbudowanym | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- directives, macros
- inline assembly, macro directives
- macros, directives
- MASM (Microsoft Macro Assembler), inline assembly macro directives
ms.assetid: 83643a09-1699-40a8-8ef2-13502bc4ac2c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cfd8e3ca5fb6bf65a288c17b1754d567b2b081a8
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
ms.locfileid: "32049854"
---
# <a name="masm-macro-directives-in-inline-assembly"></a>Dyrektywy makra MASM w zestawie wbudowanym
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Asembler wbudowany nie jest asemblera makr. Nie można użyć dyrektywy makra MASM (**makro**, `REPT`, **IRC**, `IRP`, i `ENDM`) lub makro operatory (**<>**, **!** , **&**, `%`, i `.TYPE`). `__asm` Bloku można użyć dyrektywy preprocesora C, jednak. Zobacz [przy użyciu języka C lub C++ w blokach __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md) Aby uzyskać więcej informacji.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z języka Asembler w blokach __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)