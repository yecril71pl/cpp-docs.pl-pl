---
title: Dyrektywy danych i operatory w zestawie wbudowanym
ms.date: 08/30/2018
helpviewer_keywords:
- data directives [C++]
- __asm keyword [C++], referencing limitations
- MASM (Microsoft Macro Assembler), directives
- directives [C++], MASM
- MASM (Microsoft Macro Assembler), structures
- operators [MASM]
- inline assembly, operators
- inline assembly, data directives
- MASM (Microsoft Macro Assembler), operators
- structures [C++], MASM
ms.assetid: fb7410c7-156a-4131-bcfc-211aa70533e3
ms.openlocfilehash: bcacb0cdd26181da3cf80a582866c1e30567d043
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87192356"
---
# <a name="data-directives-and-operators-in-inline-assembly"></a>Dyrektywy danych i operatory w zestawie wbudowanym

**Specyficzne dla firmy Microsoft**

Chociaż **`__asm`** blok może odwoływać się do typów danych C lub C++ i obiektów, nie może definiować obiektów danych za pomocą dyrektyw MASM lub operatorów. W szczególnych przypadkach nie można użyć definicji dyrektywy **DB**, `DW` , **DD**, `DQ` , `DT` , i `DF` ani operatora `DUP` lub. **THIS** Struktury i rekordy MASM są również niedostępne. Wbudowany asembler nie akceptuje dyrektyw `STRUC` , `RECORD` , **Width**ani **Mask**.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Korzystanie z języka zestawu w blokach __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
