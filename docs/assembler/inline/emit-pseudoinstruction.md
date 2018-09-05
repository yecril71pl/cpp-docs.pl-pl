---
title: pseudoinstrukcja _emit | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
f1_keywords:
- _emit
dev_langs:
- C++
helpviewer_keywords:
- byte defining (inline assembly)
- _emit pseudoinstruction
ms.assetid: 004c48f3-364c-4e82-9a51-e326f9cc7b2b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c8c11165e8b6632488d29e5fe79aa945332c25e9
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43689365"
---
# <a name="emit-pseudoinstruction"></a>Pseudoinstrukcja _emit

**Microsoft Specific**

**Pseudoinstrukcja** _emit definiuje jednobajtowego w bieżącej lokalizacji w bieżącym segmencie tekstu. **Pseudoinstrukcja** przypomina _emit [DB](../../assembler/masm/db.md) dyrektywę MASM.

Poniższy fragment umieszcza bajtów 0x4A 0x43 i 0x4B w kodzie:

```cpp
#define randasm __asm _emit 0x4A __asm _emit 0x43 __asm _emit 0x4B
.
.
.
__asm {
     randasm
     }
```

> [!CAUTION]
> Jeśli `_emit` generuje instrukcje, które modyfikują rejestrów i skompilować aplikację za pomocą optymalizacji, kompilator nie może określić, jakie rejestrów ma wpływ. Na przykład jeśli `_emit` generuje instrukcję, która modyfikuje **rax** rejestru, kompilator nie wie, że **rax** został zmieniony. Kompilator może następnie wprowadzić niepoprawne założeń o wartości w tym rejestrowanie po wykonaniu kodem wbudowanego asemblera. W związku z tym aplikacja może działać nieprzewidywalne zachowanie po jego uruchomieniu.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Korzystanie z języka Asembler w blokach __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>