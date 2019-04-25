---
title: Definiowanie bloków __asm jako makr C
ms.date: 08/30/2018
helpviewer_keywords:
- macros, __asm blocks
- Visual C, macros
- __asm keyword [C++], as C macros
ms.assetid: 677ba11c-21c8-4609-bba7-cd47312243b0
ms.openlocfilehash: c48298cf802600995dbbf68885896b6feccb807d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167029"
---
# <a name="defining-asm-blocks-as-c-macros"></a>Definiowanie bloków __asm jako makr C

**Microsoft Specific**

Makr C, oferuje wygodny sposób, aby wstawić kod zestawu do kodu źródłowego, ale wymagają ostrożność, ponieważ makro rozszerzy się na jednym wierszu logicznym. Aby utworzyć bezproblemowej makra, należy wykonać następujące czynności:

- Ujmij `__asm` bloku w nawiasach klamrowych.

- Umieść `__asm` — słowo kluczowe przed każdą instrukcję montażu.

- Użyj komentarze języka C w starym stylu ( `/* comment */`) zamiast zestawu w stylu ( `; comment`) lub jeden wiersz komentarze języka C ( `// comment`).

Aby zilustrować, w poniższym przykładzie zdefiniowano proste makra:

```cpp
#define PORTIO __asm      \
/* Port output */         \
{                         \
   __asm mov al, 2        \
   __asm mov dx, 0xD007   \
   __asm out dx, al       \
}
```

Na pierwszy rzut oka ostatnich trzech `__asm` słowa kluczowe wydają się zbędne. Są one potrzebne, jednak ponieważ makro rozszerza się w jednym wierszu:

```cpp
__asm /* Port output */ { __asm mov al, 2  __asm mov dx, 0xD007 __asm out dx, al }
```

Trzecia i czwarta `__asm` słowa kluczowe są wymagane jako separatory instrukcji. Separatory jedyną instrukcją rozpoznawany w `__asm` bloki są znak nowego wiersza i `__asm` — słowo kluczowe. Ponieważ blok, który został zdefiniowany jako makro jest jednym wierszu logicznym, muszą być rozdzielone każdą instrukcję przy użyciu `__asm`.

Nawiasy klamrowe są również istotne. Jeśli je pominiesz, kompilator może mylące instrukcje C i C++, w tym samym wierszu z prawej strony wywołanie makra. Bez zamykającego nawiasu klamrowego, kompilator nie wiadomo, gdzie kod zestawu zatrzymuje się i widzi instrukcje C i C++ `__asm` bloku jako zestaw instrukcji.

Komentarze stylu zestawu, rozpoczynające się od średnika (**;**) przejdź do końca wiersza. To powoduje problemy w makrach, ponieważ kompilator ignoruje całą zawartość po komentarzu, aż do końca wiersza logiczne. To samo dotyczy programu Komentarze jednowierszowe C lub C++ ( `// comment`). Aby uniknąć błędów, należy użyć komentarze języka C w starym stylu ( `/* comment */`) w `__asm` bloki określone jako makra.

`__asm` Bloku pisane jako makr C może potrwać argumentów. W odróżnieniu od zwykłego C — makro, jednak `__asm` — makro nie może zwracać wartości. Dlatego takie makra nie można używać w wyrażeniach języka C lub C++.

Uważaj, aby nie masowe wywołania makra tego typu. Na przykład, wywołanie makra języka zestawu w funkcji zadeklarowanych za pomocą `__fastcall` Konwencji może spowodować nieoczekiwane wyniki. (Zobacz [za pomocą rejestrów i zachowywanie ich w asemblerze wbudowanym](../../assembler/inline/using-and-preserving-registers-in-inline-assembly.md).)

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Wbudowany asembler](../../assembler/inline/inline-assembler.md)<br/>