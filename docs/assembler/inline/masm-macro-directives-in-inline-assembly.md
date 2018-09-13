---
title: Dyrektywy makra MASM w zestawie wbudowanym | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
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
ms.openlocfilehash: 35ad22a9a4b79a31665ab6b156f8174d395bb0ee
ms.sourcegitcommit: fb9448eb96c6351a77df04af16ec5c0fb9457d9e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "43687976"
---
# <a name="masm-macro-directives-in-inline-assembly"></a>Dyrektywy makra MASM w zestawie wbudowanym

**Microsoft Specific**

Wbudowany asembler nie jest asemblera makr. Nie można użyć dyrektywy makra MASM (**— makro**, `REPT`, **IRC**, `IRP`, i `ENDM`) lub makro operatorów (**<>**, **!** , **&**, `%`, i `.TYPE`). `__asm` Bloku można użyć dyrektywy preprocesora C, jednak. Zobacz [przy użyciu języka C lub C++ w blokach __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md) Aby uzyskać więcej informacji.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Korzystanie z języka Asembler w blokach __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>