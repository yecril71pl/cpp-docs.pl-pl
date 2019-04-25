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
ms.openlocfilehash: 5c07fa897da23a55f376a20e7588c8c8c269d1a6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167377"
---
# <a name="segment-references-in-inline-assembly"></a>Odwołania do segmentu w zestawie wbudowanym

**Microsoft Specific**

Konieczne jest odwołanie się do segmentów rejestru, a nie nazwy (Nazwa segmentu `_TEXT` jest nieprawidłowy, na przykład). Segment zastąpień należy użyć rejestru jawnie, tak jak ES: [BX].

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Korzystanie z języka Asembler w blokach __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>