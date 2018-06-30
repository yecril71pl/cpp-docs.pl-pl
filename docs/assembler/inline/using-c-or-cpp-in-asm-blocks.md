---
title: Przy użyciu języka C lub C++ w blokach __asm | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/25/2018
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
ms.openlocfilehash: 96ed46cdf44ccacee806dd03bf7eacca26eec32d
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120953"
---
# <a name="using-c-or-c-in-asm-blocks"></a>Korzystanie z C lub C++ w blokach __asm

** Firmy Microsoft dotyczące **

Ponieważ wbudowany zestaw instrukcji można łączyć w instrukcjach języka C lub C++, mogą odwoływać się do zmiennych C lub C++ według nazwy i używać wiele elementów z tych języków.

`__asm` Bloku można użyć następujących elementów języka:

- Symbole, w tym etykiety i nazwy zmiennych i funkcji

- Stałe, włączając stałe symboliczne i `enum` elementy członkowskie

- Makra i dyrektywy preprocesora

- Komentarze (zarówno __/ \* \* /__ i __//__ )

- Wpisz nazwy (wszędzie tam, gdzie typ MASM byłoby prawne)

- `typedef` nazwy, zazwyczaj używane przy użyciu operatorów takich jak **PTR** i **typu** lub określić elementy członkowskie struktury lub związku

W ramach `__asm` bloku, stałe całkowite można określić za pomocą notacji C lub notacji podstawa asemblera (0x100 i 100 h są równoważne, na przykład). Dzięki temu można określić (przy użyciu `#define`) stała w języku C i używać go w części C lub C++ i zestawu programu. Można również określić stałe w ósemkowe poprzedzając od 0. Na przykład 0777 określa ósemkowe stała.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?

- [Używanie operatorów w blokach __asm](../../assembler/inline/using-operators-in-asm-blocks.md)

- [Przy użyciu języka C lub C++ Symbols_in bloków __asm](../../assembler/inline/using-c-or-cpp-symbols-in-asm-blocks.md)

- [Uzyskiwanie dostępu do danych C lub C++ w blokach __asm](../../assembler/inline/accessing-c-or-cpp-data-in-asm-blocks.md)

- [Pisanie funkcji w zestawie wbudowanym](../../assembler/inline/writing-functions-with-inline-assembly.md)

**KOŃCOWY określonych firmy Microsoft**

## <a name="see-also"></a>Zobacz także

[Wbudowany asembler](../../assembler/inline/inline-assembler.md)
