---
title: __asm
ms.date: 10/09/2018
f1_keywords:
- __asm
- _asm
- __asm_cpp
helpviewer_keywords:
- __asm keyword [C++], vs. asm blocks
- __asm keyword [C++]
ms.assetid: 77ff3bc9-a492-4b5e-85e1-fa4e414e79cd
ms.openlocfilehash: 43c7ae02e465ce8de2871d78e7ba604221aa7426
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2019
ms.locfileid: "65445899"
---
# <a name="asm"></a>__asm

**Microsoft Specific**

`__asm` — Słowo kluczowe wywoła asembler wbudowany i może znajdować się wszędzie tam, gdzie instrukcja C lub C++ jest legalna. Nie może występować samodzielnie. Jego musi następować instrukcja zestawu, grupa instrukcji ujęta w nawiasy klamrowe, lub co najmniej, para pustych nawiasów klamrowych. Termin "`__asm` blok" odnosi się tutaj do każdej instrukcji lub grupy instrukcji, czy w nawiasach klamrowych.

> [!NOTE]
> Obsługa Visual C++ dla Standard C++ `asm` — słowo kluczowe jest ograniczone faktem, że kompilator nie wygeneruje błędu na słowie kluczowym. Jednak `asm` bloku nie wygeneruje istotnego kodu. Użyj `__asm` zamiast `asm`.

## <a name="grammar"></a>Gramatyka

*Blok Asm*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__asm** *instrukcji montażu* **;** <sub>zoptymalizowany pod kątem</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__asm {** *instrukcji montażu* **}** **;** <sub>zoptymalizowany pod kątem</sub>

*instrukcji montażu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrukcji montażu* **;** <sub>zoptymalizowany pod kątem</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrukcji montażu* **;** *instrukcji montażu* **;** <sub>zoptymalizowany pod kątem</sub>

## <a name="remarks"></a>Uwagi

Jeśli używana bez nawiasów klamrowych, `__asm` — słowo kluczowe oznacza, że pozostała część wiersza jest instrukcją języka asemblera. Jeśli używana z nawiasami klamrowymi, oznacza to, że każdy wiersz między nawiasami jest instrukcją języka asemblera. W celu zgodności z poprzednimi wersjami `_asm` jest synonimem dla `__asm`.

Ponieważ `__asm` — słowo kluczowe jest separatorem instrukcji, instrukcje zestawu można umieścić w tym samym wierszu.

Przed Visual Studio 2005, instrukcja

```cpp
__asm int 3
```

nie spowodował, że kod natywny wygenerowany, gdy skompilowano z opcją **/CLR**; kompilator przetłumaczył instrukcje do instrukcji przerwy CLR.

`__asm int 3` teraz powoduje generowanie kodu natywnego dla funkcji. Jeśli chcesz, aby funkcja wywoływała przerwę w kodzie i tę funkcję skompilować do MSIL, należy użyć [__debugbreak](../../intrinsics/debugbreak.md).

W celu zgodności z poprzednimi wersjami **_asm** jest synonimem dla **__asm** chyba że — opcja kompilatora [/Za \(Wyłącz rozszerzenia językowe)](../../build/reference/za-ze-disable-language-extensions.md) jest określony.

## <a name="example"></a>Przykład

Poniższy fragment kodu jest prostą `__asm` bloku ujęte w nawiasy klamrowe:

```cpp
__asm {
   mov al, 2
   mov dx, 0xD007
   out dx, al
}
```

Alternatywnie, możesz umieścić `__asm` przed każdą instrukcję montażu:

```cpp
__asm mov al, 2
__asm mov dx, 0xD007
__asm out dx, al
```

Ponieważ `__asm` — słowo kluczowe jest separatorem instrukcji, instrukcje zestawu można także umieścić w tym samym wierszu:

```cpp
__asm mov al, 2   __asm mov dx, 0xD007   __asm out dx, al
```

Wszystkie trzy przykłady generują ten sam kod, ale pierwszy stylu (załączanie `__asm` bloku w nawiasach klamrowych) ma kilka zalet. Nawiasy klamrowe wyraźnie oddzielają kodu zestawu od kodu C lub C++ i pozwalają uniknąć powtórzenia niepotrzebnego `__asm` — słowo kluczowe. Nawiasy klamrowe mogą również zapobiec niejasności. Jeśli chcesz umieścić instrukcję C lub C++ w tym samym wierszu, co `__asm` bloku, blok należy ująć w nawiasy klamrowe. Bez nawiasów klamrowych kompilator nie wiadomo, gdzie rozpocząć kod zestawu zatrzymuje i instrukcje C i C++. Na koniec ponieważ tekst w nawiasach klamrowych ma ten sam format jak zwykły tekst MASM, można łatwo wyciąć i wkleić tekst z istniejących plików źródłowych MASM.

W odróżnieniu od nawiasów klamrowych w C i C++, nawiasy klamrowe obejmujące `__asm` bloku nie mają wpływu na zakres zmiennej. Można także zagnieżdżać `__asm` bloki; zagnieżdżanie nie ma wpływu na zakres zmiennej.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../../cpp/keywords-cpp.md)<br/>
[Wbudowany asembler](../../assembler/inline/inline-assembler.md)<br/>