---
title: Użycie symboli C lub C++ w blokach __asm
ms.date: 08/30/2018
helpviewer_keywords:
- __asm keyword [C++], syntax
- symbols, in __asm blocks
- Visual C, symbols in __asm blocks
- __asm keyword [C++], C/C++ elements in
- Visual C++, in __asm blocks
ms.assetid: 0758ffdc-dfe9-41c8-a5e1-fd395bcac328
ms.openlocfilehash: fd9f8b444d263818aca1b16260f70730d5350e7c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169113"
---
# <a name="using-c-or-c-symbols-in-__asm-blocks"></a>Użycie symboli C lub C++ w blokach __asm

**Specyficzne dla firmy Microsoft**

Blok `__asm` może odwoływać się do dowolnego języka C++ C lub symbolu w zakresie, w którym znajduje się blok. (C i C++ symbole są nazwami zmiennych, nazwami funkcji i etykietami, czyli nazwami, które nie są symbolicznymi ani elementami członkowskimi `enum`. Nie można wywołać C++ funkcji Członkowskich.)

Istnieją pewne ograniczenia dotyczące używania języka C i C++ symboli:

- Każda instrukcja języka asemblera może zawierać tylko jeden znak C C++ lub. Wiele symboli może występować w tej samej instrukcji zestawu tylko z wyrażeniami **długości**, **typu**i **rozmiaru** .

- Funkcje, do których odwołuje się blok `__asm`, muszą być zadeklarowane we wcześniejszej części tego programu. W przeciwnym razie kompilator nie może rozróżnić nazw funkcji i etykiet w bloku `__asm`.

- Blok `__asm` nie może używać żadnych znaków C C++ ani symboli mających takie same pisownia jak słowa zastrzeżone MASM (bez względu na wielkość liter). Słowa zastrzeżone MASM zawierają nazwy instrukcji, takie jak **push** i Register Names, takie jak si.

- Tagi struktury i Unii nie są rozpoznawane w blokach `__asm`.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Korzystanie z C lub C++ w blokach __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
