---
title: Odwołania do segmentu w zestawie wbudowanym
ms.date: 08/30/2018
helpviewer_keywords:
- references, inline assembly
- segment references in inline assembly
- inline assembly, segment references
- registers
- inline assembly, registers
- registers, inline assembly
ms.assetid: c63e6bb4-49d9-4fa1-bb22-eea21b5cbc0f
ms.openlocfilehash: 865fc5fac5f46cdc8c55966e9989227d1d671d6f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169256"
---
# <a name="segment-references-in-inline-assembly"></a>Odwołania do segmentu w zestawie wbudowanym

**Specyficzne dla firmy Microsoft**

Należy odwołać się do segmentów, rejestrując zamiast nazwy (nazwa segmentu `_TEXT` jest nieprawidłowa, na przykład). Zastąpienia segmentu muszą używać rejestru jawnie, jak w ES: [BX].

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Korzystanie z języka Asembler w blokach __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
