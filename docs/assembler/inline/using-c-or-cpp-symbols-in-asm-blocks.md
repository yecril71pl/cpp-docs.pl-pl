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
ms.openlocfilehash: fc22af8ec04d616eb8f5566b118e19c405605401
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552519"
---
# <a name="using-c-or-c-symbols-in-asm-blocks"></a>Użycie symboli C lub C++ w blokach __asm

**Microsoft Specific**

`__asm` Bloku mogą odwoływać się do żadnych symboli C lub C++ w zakresie, gdzie pojawia się blok. (Symbole C i C++ są nazwy zmiennych, nazwy funkcji i etykiet; czyli, nazw, które nie należy stosować stałe symboliczne lub `enum` elementów członkowskich. Nie można wywołać składowych języka C++ funkcji.)

Kilku ograniczeniom użycie symboli C i C++:

- Każda instrukcja języka asembler może zawierać tylko jeden C lub C++ symbolu. Wiele symboli może znajdować się w tej samej instrukcji montażu tylko w przypadku **długość**, **typu**, i **rozmiar** wyrażenia.

- Funkcje, do którego odwołuje się `__asm` bloku musi być zadeklarowana we wcześniejszej części programu (prototypowane). W przeciwnym razie kompilator nie rozróżnia między nazwami funkcji i etykiety w `__asm` bloku.

- `__asm` Bloku nie można używać żadnych symboli C lub C++ przy użyciu tej samej pisowni jako słowa zastrzeżone MASM (niezależnie od wielkości liter). Słowa zastrzeżone MASM obejmują instrukcji nazwy, takie jak **WYPYCHANIA** i Zarejestruj nazwy, takie jak SI.

- Tagi struktury i Unii nie są rozpoznawane w `__asm` bloków.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Korzystanie z C lub C++ w blokach __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>