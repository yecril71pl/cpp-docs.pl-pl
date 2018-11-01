---
title: Dyrektywy makra MASM w zestawie wbudowanym
ms.date: 08/30/2018
helpviewer_keywords:
- directives, macros
- inline assembly, macro directives
- macros, directives
- MASM (Microsoft Macro Assembler), inline assembly macro directives
ms.assetid: 83643a09-1699-40a8-8ef2-13502bc4ac2c
ms.openlocfilehash: 7e1bed782d28a5bf7c934c3f57f50aae70038578
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508930"
---
# <a name="masm-macro-directives-in-inline-assembly"></a>Dyrektywy makra MASM w zestawie wbudowanym

**Microsoft Specific**

Wbudowany asembler nie jest asemblera makr. Nie można użyć dyrektywy makra MASM (**— makro**, `REPT`, **IRC**, `IRP`, i `ENDM`) lub makro operatorów (**<>**, **!** , **&**, `%`, i `.TYPE`). `__asm` Bloku można użyć dyrektywy preprocesora C, jednak. Zobacz [przy użyciu języka C lub C++ w blokach __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md) Aby uzyskać więcej informacji.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Korzystanie z języka Asembler w blokach __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>