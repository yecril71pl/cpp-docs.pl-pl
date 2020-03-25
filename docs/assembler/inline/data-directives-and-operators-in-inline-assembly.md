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
ms.openlocfilehash: 916dce0346bebfc5ff65ca558ae75317a187660a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169542"
---
# <a name="data-directives-and-operators-in-inline-assembly"></a>Dyrektywy danych i operatory w zestawie wbudowanym

**Specyficzne dla firmy Microsoft**

Chociaż blok `__asm` może odwoływać się do C++ typów danych C lub i obiektów, nie może definiować obiektów danych za pomocą dyrektyw MASM lub operatorów. W przeciwnym razie nie można używać definicji dyrektyw **DB**, `DW`, **DD**, `DQ`, `DT`i **`DF`ani operatorów `DUP` lub.** Struktury i rekordy MASM są również niedostępne. Wbudowany asembler nie akceptuje dyrektyw `STRUC`, `RECORD`, **Width**ani **Mask**.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Korzystanie z języka Asembler w blokach __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
