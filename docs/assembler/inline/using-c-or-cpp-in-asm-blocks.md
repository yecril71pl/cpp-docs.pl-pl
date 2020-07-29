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
ms.openlocfilehash: 05e63d666f3fc39126d6f48e8fc523c4a02e76df
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87191420"
---
# <a name="using-c-or-c-in-__asm-blocks"></a>Korzystanie z C lub C++ w blokach __asm

**Specyficzne dla firmy Microsoft**

Ponieważ instrukcje wbudowanego zestawu mogą być mieszane przy użyciu instrukcji C lub C++, mogą odwoływać się do zmiennych C lub C++ według nazwy i korzystać z wielu innych elementów języków.

**`__asm`** Blok może używać następujących elementów języka:

- Symbole, w tym etykiety i nazwy zmiennych i funkcji

- Stałe, w tym stałe symboliczne i **`enum`** elementy członkowskie

- Makra i dyrektywy preprocesora

- Komentarze ( __ / \* \* zarówno / __ i __//__ )

- Nazwy typów (wszędzie tam, gdzie typ MASM byłby dozwolony)

- **`typedef`** nazwy, zwykle używane z operatorami, takimi jak **PTR** i **Type** lub do określania struktury lub składowych Unii

W **`__asm`** bloku można określić stałe całkowite przy użyciu notacji C lub asemblera podstawy (0x100 i 100h są równoważne, na przykład). Pozwala to definiować (za pomocą `#define` ) stałą w c, a następnie używać jej zarówno w języku c, jak i w części zestawu programu. Możesz również określić stałe w liczbie ósemkowej, poprzedzając je wartością 0. Na przykład 0777 określa stałą ósemkową.

## <a name="what-do-you-want-to-know-more-about"></a>Jak chcesz dowiedzieć się więcej?

- [Używanie operatorów w blokach __asm](../../assembler/inline/using-operators-in-asm-blocks.md)

- [Korzystanie z bloków __asm w języku C lub C++ Symbols_in](../../assembler/inline/using-c-or-cpp-symbols-in-asm-blocks.md)

- [Uzyskiwanie dostępu do danych C lub C++ w blokach __asm](../../assembler/inline/accessing-c-or-cpp-data-in-asm-blocks.md)

- [Pisanie funkcji w zestawie wbudowanym](../../assembler/inline/writing-functions-with-inline-assembly.md)

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Asembler wbudowany](../../assembler/inline/inline-assembler.md)<br/>
