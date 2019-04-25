---
title: Korzystanie z C lub C++ w blokach __asm
ms.date: 08/30/2018
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
ms.openlocfilehash: 0949eba769bed33da8fe39bb41500a2ba02af224
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166558"
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
