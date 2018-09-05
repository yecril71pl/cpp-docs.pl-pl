---
title: Korzystanie z C lub C++ w blokach __asm | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inline assembly, mixing instructions with C/C++ statements
- symbols, in __asm blocks
- macros, __asm blocks
- preprocessor directives, used in __asm blocks
- type names, used in __asm blocks
- preprocessor directives
- preprocessor, directives
- constants, in __asm blocks
- comments, in __asm blocks
- typedef names, used in __asm blocks
- __asm keyword [C++], C/C++ elements in
ms.assetid: ae8b2b52-6b75-42e3-ac0c-ad02d922ed97
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 14b91a7925089f6a6ab747a9fd6a5813f9a14693
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43687102"
---
# <a name="using-c-or-c-in-asm-blocks"></a>Korzystanie z C lub C++ w blokach __asm

** Specyficzne dla firmy Microsoft **

Ponieważ instrukcje montażu w tekście mogą być mieszane w instrukcjach języka C lub C++, mogą odwoływać się do zmiennych C lub C++ według nazwy i korzystać z wielu elementów z tych języków.

`__asm` Bloku można użyć następujących elementów języka:

- Symbole, w tym etykiety i nazwy zmiennych i funkcji

- Stałe łącznie ze stałymi symbolicznymi i `enum` elementy członkowskie

- Makra i dyrektywy preprocesora

- Komentarze (zarówno __/ \* \* /__ i __//__ )

- Wpisz nazwy użytkowników (wszędzie tam, gdzie typ MASM będą prawne)

- `typedef` nazwy, ogólnie takie jak używane z operatorów **PTR** i **typu** lub określić elementy członkowskie struktury lub Unii

W ramach `__asm` bloku, można określić stałe całkowite przy użyciu notacji języka C lub notacji podstawy asemblera (0x100 do 100 h są równoważne, na przykład). Dzięki temu można zdefiniować (przy użyciu `#define`) stałą w języku C, a następnie użyj w C lub C++ i zestawu części programu. Można również określić stałe w ósemkowej poprzedzając je z 0. Na przykład 0777 określa stałą ósemkową.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

- [Używanie operatorów w blokach __asm](../../assembler/inline/using-operators-in-asm-blocks.md)

- [Przy użyciu języka C lub C++ Symbols_in blokach __asm](../../assembler/inline/using-c-or-cpp-symbols-in-asm-blocks.md)

- [Uzyskiwanie dostępu do danych C lub C++ w blokach __asm](../../assembler/inline/accessing-c-or-cpp-data-in-asm-blocks.md)

- [Pisanie funkcji w zestawie wbudowanym](../../assembler/inline/writing-functions-with-inline-assembly.md)

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Wbudowany asembler](../../assembler/inline/inline-assembler.md)<br/>
