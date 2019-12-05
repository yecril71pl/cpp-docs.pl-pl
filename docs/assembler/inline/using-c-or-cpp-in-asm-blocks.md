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
ms.openlocfilehash: 16b298b92a4ba40d9091499a1821ad4f3c413d6c
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74854527"
---
# <a name="using-c-or-c-in-__asm-blocks"></a>Korzystanie z C lub C++ w blokach __asm

**Microsoft Specific**

Ponieważ instrukcje wbudowanego zestawu mogą być mieszane z C C++ lub instrukcjami, mogą odwoływać się C++ do c lub zmienne według nazwy i używać wielu innych elementów języków.

Blok `__asm` może używać następujących elementów języka:

- Symbole, w tym etykiety i nazwy zmiennych i funkcji

- Stałe, w tym stałe symboliczne i `enum` elementy członkowskie

- Makra i dyrektywy preprocesora

- Komentarze (zarówno __/\* \*/__ i __//__ )

- Nazwy typów (wszędzie tam, gdzie typ MASM byłby dozwolony)

- nazwy `typedef`, zwykle używane z operatorami, takimi jak **PTR** i **Type** , lub w celu określenia struktury lub składowych Unii

W bloku `__asm` można określić stałe całkowite przy użyciu notacji C lub asemblera podstawy (0x100 i 100h są równoważne, na przykład). Pozwala to definiować (przy użyciu `#define`) stałą w C, a następnie używać jej zarówno w części C, C++ jak i w zestawie. Możesz również określić stałe w liczbie ósemkowej, poprzedzając je wartością 0. Na przykład 0777 określa stałą ósemkową.

## <a name="what-do-you-want-to-know-more-about"></a>O czym chcesz się dowiedzieć więcej?

- [Używanie operatorów w blokach __asm](../../assembler/inline/using-operators-in-asm-blocks.md)

- [Korzystanie z bloków C++ __asm C lub Symbols_in](../../assembler/inline/using-c-or-cpp-symbols-in-asm-blocks.md)

- [Uzyskiwanie dostępu do danych C lub C++ w blokach __asm](../../assembler/inline/accessing-c-or-cpp-data-in-asm-blocks.md)

- [Pisanie funkcji w zestawie wbudowanym](../../assembler/inline/writing-functions-with-inline-assembly.md)

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Wbudowany asembler](../../assembler/inline/inline-assembler.md)<br/>
