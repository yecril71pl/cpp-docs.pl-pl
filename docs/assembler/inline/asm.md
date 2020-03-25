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
ms.openlocfilehash: de28e4c0fad6b89a62b4479c5c32f0b8606cf3af
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169634"
---
# <a name="__asm"></a>__asm

**Specyficzne dla firmy Microsoft**

Słowo kluczowe `__asm` wywołuje wbudowany asembler i może występować wszędzie tam, gdzie C++ jest to dozwolone. Nie może być wyświetlana sama przez siebie. Po nim musi następować instrukcja zestawu, Grupa instrukcji ujętych w nawiasy klamrowe lub, co najmniej, pustą parę nawiasów klamrowych. Termin "`__asm` blok" odnosi się do dowolnej instrukcji lub grupy instrukcji, niezależnie od tego, czy znajdują się w nawiasach klamrowych.

> [!NOTE]
> Obsługa C++ wizualizacji dla standardowego C++ słowa kluczowego `asm` jest ograniczona do faktu, że kompilator nie generuje błędu dla słowa kluczowego. Jednak blok `asm` nie będzie generował żadnego kodu znaczącego. Użyj `__asm`, a nie `asm`.

## <a name="grammar"></a>Gramatyka

*ASM — blok*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__asm** *instrukcji zestawu* **;** <sub>wybór</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__asm {** *zestaw instrukcji-list* **}** **;** <sub>wybór</sub>

*instrukcja Assembly-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrukcji zestawu* **;** <sub>wybór</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrukcji zestawu* **;** *Lista instrukcji zestawu* **;** <sub>wybór</sub>

## <a name="remarks"></a>Uwagi

Jeśli jest używany bez nawiasów klamrowych, `__asm` słowo kluczowe oznacza, że pozostała część wiersza jest instrukcją języka asemblera. W przypadku użycia z nawiasami klamrowymi oznacza, że każdy wiersz między nawiasami jest instrukcją języka asemblera. W celu zapewnienia zgodności z poprzednimi wersjami `_asm` jest synonimem `__asm`.

Ponieważ `__asm` słowo kluczowe jest separatorem instrukcji, można umieścić instrukcje zestawu w tym samym wierszu.

Przed dodaniem programu Visual Studio 2005, instrukcja

```cpp
__asm int 3
```

nie powoduje, że kod natywny został wygenerowany po skompilowaniu z **/CLR**; Kompilator przetłumaczy instrukcję do instrukcji break środowiska CLR.

`__asm int 3` teraz spowoduje generowanie kodu natywnego dla funkcji. Jeśli chcesz, aby funkcja powodowała punkt przerwania w kodzie i jeśli chcesz, aby ta funkcja była skompilowana do MSIL, użyj [__debugbreak](../../intrinsics/debugbreak.md).

W celu zapewnienia zgodności z poprzednimi wersjami **_asm** jest synonimem dla **__asm** , chyba że opcja kompilatora [/za \(Wyłącz rozszerzenia językowe)](../../build/reference/za-ze-disable-language-extensions.md) .

## <a name="example"></a>Przykład

Poniższy fragment kodu jest prostym blokiem `__asm` w nawiasach klamrowych:

```cpp
__asm {
   mov al, 2
   mov dx, 0xD007
   out dx, al
}
```

Alternatywnie można umieścić `__asm` przed każdą instrukcją zestawu:

```cpp
__asm mov al, 2
__asm mov dx, 0xD007
__asm out dx, al
```

Ponieważ `__asm` słowo kluczowe jest separatorem instrukcji, można również umieścić instrukcje zestawu w tym samym wierszu:

```cpp
__asm mov al, 2   __asm mov dx, 0xD007   __asm out dx, al
```

Wszystkie trzy przykłady generują ten sam kod, ale pierwszy styl (otaczający blok `__asm` w nawiasach klamrowych) ma pewne zalety. Nawiasy klamrowe wyraźnie oddzielają kod zestawu od C++ C lub Code i unikają niepotrzebnego powtórzenia słowa kluczowego `__asm`. Nawiasy klamrowe mogą również uniemożliwić niejasności. Jeśli chcesz umieścić instrukcję C lub C++ w tym samym wierszu co blok `__asm`, należy ująć blok w nawiasy klamrowe. Bez nawiasów klamrowych kompilator nie może stwierdzić, gdzie kod zestawu zostaje zatrzymany C++ , a instrukcja C lub Begins. Na koniec, ponieważ tekst w nawiasach ma taki sam format jak zwykły tekst MASM, można łatwo wyciąć i wkleić tekst z istniejących plików źródłowych MASM.

W przeciwieństwie do nawiasów klamrowych w języku C i C++nawiasy klamrowe otaczające blok `__asm` nie wpływają na zakres zmiennej. Można również zagnieżdżać bloki `__asm`; zagnieżdżanie nie ma wpływu na zakres zmiennej.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Słowa kluczowe](../../cpp/keywords-cpp.md)<br/>
[Wbudowany asembler](../../assembler/inline/inline-assembler.md)<br/>
