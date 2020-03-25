---
title: Dyrektywy makra MASM w zestawie wbudowanym
ms.date: 08/30/2018
helpviewer_keywords:
- directives, macros
- inline assembly, macro directives
- macros, directives
- MASM (Microsoft Macro Assembler), inline assembly macro directives
ms.assetid: 83643a09-1699-40a8-8ef2-13502bc4ac2c
ms.openlocfilehash: 38b73346fc52f6b5efe478f8eb960ad049fae924
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169282"
---
# <a name="masm-macro-directives-in-inline-assembly"></a>Dyrektywy makra MASM w zestawie wbudowanym

**Specyficzne dla firmy Microsoft**

Asembler wbudowany nie jest asemblerem makra. Nie można użyć dyrektyw makra MASM (**Macro**, `REPT`, **IRC**, `IRP`i `ENDM`) ani operatorów makr ( **<>** , **!** , **&** , `%`i `.TYPE`). Blok `__asm` może jednak korzystać z dyrektyw preprocesora języka C. Aby uzyskać więcej informacji [, zobacz Używanie języka C C++ lub bloków __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md) .

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Korzystanie z języka Asembler w blokach __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
