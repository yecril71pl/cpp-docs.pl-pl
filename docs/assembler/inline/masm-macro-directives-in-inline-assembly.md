---
title: Dyrektywy makra MASM w zestawie wbudowanym
ms.date: 08/30/2018
helpviewer_keywords:
- directives, macros
- inline assembly, macro directives
- macros, directives
- MASM (Microsoft Macro Assembler), inline assembly macro directives
ms.assetid: 83643a09-1699-40a8-8ef2-13502bc4ac2c
ms.openlocfilehash: 964f70aeef6e0e62ac4b941b2cc26d3e7c7ef466
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87191798"
---
# <a name="masm-macro-directives-in-inline-assembly"></a>Dyrektywy makra MASM w zestawie wbudowanym

**Specyficzne dla firmy Microsoft**

Asembler wbudowany nie jest asemblerem makra. Nie można użyć dyrektyw makra MASM (**makra**, `REPT` , **IRC**, `IRP` i `ENDM` ) lub operatorów makr ( **<>** , **!**, **&** , `%` i `.TYPE` ). **`__asm`** Blok może jednak korzystać z dyrektyw preprocesora języka C. Aby uzyskać więcej informacji [, zobacz Używanie języka C lub C++ w blokach __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md) .

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Korzystanie z języka zestawu w blokach __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
