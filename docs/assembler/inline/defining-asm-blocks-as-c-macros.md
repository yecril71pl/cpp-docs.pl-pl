---
title: Definiowanie bloków __asm jako makr C
ms.date: 08/30/2018
helpviewer_keywords:
- macros, __asm blocks
- Visual C, macros
- __asm keyword [C++], as C macros
ms.assetid: 677ba11c-21c8-4609-bba7-cd47312243b0
ms.openlocfilehash: 46f0a23fcfd949843e3548354f52970b10b6d63b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169490"
---
# <a name="defining-__asm-blocks-as-c-macros"></a>Definiowanie bloków __asm jako makr C

**Specyficzne dla firmy Microsoft**

Makra języka C oferują wygodną metodę wstawiania kodu zestawu do kodu źródłowego, ale wymagają one dodatkowej opieki, ponieważ makro rozszerza się w jedną linię logiczną. Aby utworzyć makra bez problemów, wykonaj następujące reguły:

- Umieść blok `__asm` w nawiasach klamrowych.

- Umieść słowo kluczowe `__asm` przed każdą instrukcją zestawu.

- Używaj w starym miejscu komentarzy języka C (`/* comment */`) zamiast komentarzy w stylu zestawu (`; comment`) lub komentarzy w języku C (`// comment`).

W poniższym przykładzie zdefiniowano proste makro:

```cpp
#define PORTIO __asm      \
/* Port output */         \
{                         \
   __asm mov al, 2        \
   __asm mov dx, 0xD007   \
   __asm out dx, al       \
}
```

Na pierwszy rzut oka ostatnie trzy słowa kluczowe `__asm` są pozornie zbędne. Są one jednak zbędne, ponieważ makro rozszerza się w jeden wiersz:

```cpp
__asm /* Port output */ { __asm mov al, 2  __asm mov dx, 0xD007 __asm out dx, al }
```

Trzy i czwarte `__asm` słów kluczowych są zbędne jako separatory instrukcji. Jedyne separatory instrukcji rozpoznawane w blokach `__asm` są znakiem nowego wiersza i `__asm` słowem kluczowym. Ponieważ blok zdefiniowany jako makro jest jedną linią logiczną, należy oddzielić każdą instrukcję `__asm`.

Nawiasy klamrowe są również niezbędne. Jeśli zostaną pominięte, kompilator może być pomylony przez C C++ lub instrukcji w tym samym wierszu z prawej strony wywołania makra. Bez zamykającego nawiasu klamrowego kompilator nie może stwierdzić, gdzie jest zatrzymywany kod zestawu i widzi C++ C lub instrukcji po bloku `__asm` jako instrukcje zestawu.

Komentarze w stylu zestawu, które zaczynają się średnikiem ( **;** ), przejdź do końca wiersza. Powoduje to problemy z makrami, ponieważ kompilator ignoruje wszystko po komentarzu, aż do końca linii logicznej. To samo jest prawdziwe w przypadku pojedynczych wierszy C lub C++ comments (`// comment`). Aby zapobiec błędom, należy użyć starych stylów języka C (`/* comment */`) w blokach `__asm` zdefiniowanych jako makra.

Blok `__asm` zapisany jako makro C może przyjmować argumenty. W przeciwieństwie do zwykłego makra C, jednak makro `__asm` nie może zwrócić wartości. Dlatego nie można używać takich makr w wyrażeniach C++ C i.

Należy zachować ostrożność, aby nie wywoływać makr tego typu. Na przykład wywoływanie makra języka zestawu w funkcji zadeklarowanej z Konwencją `__fastcall` może spowodować nieoczekiwane wyniki. (Zobacz [Używanie i zachowywanie rejestrów w zestawie wbudowanym](../../assembler/inline/using-and-preserving-registers-in-inline-assembly.md)).

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Wbudowany asembler](../../assembler/inline/inline-assembler.md)<br/>
