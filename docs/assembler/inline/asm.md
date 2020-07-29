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
ms.openlocfilehash: 14a40bef5b2edba76fc130604414c45eee589bcd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87193006"
---
# `__asm`

**Specyficzne dla firmy Microsoft**

**`__asm`** Słowo kluczowe wywołuje asembler wbudowany i może występować wszędzie tam, gdzie instrukcja C lub C++ ma charakter prawny. Nie może być wyświetlana sama przez siebie. Po nim musi następować instrukcja zestawu, Grupa instrukcji ujętych w nawiasy klamrowe lub, co najmniej, pustą parę nawiasów klamrowych. Termin " **`__asm`** blok" odnosi się do dowolnej instrukcji lub grupy instrukcji, niezależnie od tego, czy znajdują się w nawiasach klamrowych.

> [!NOTE]
> Visual C++ Obsługa standardowego **`asm`** słowa kluczowego języka C++ jest ograniczona do faktu, że kompilator nie generuje błędu dla słowa kluczowego. Jednak **`asm`** blok nie będzie generował żadnego kodu znaczącego. Użyj **`__asm`** zamiast **`asm`** .

## <a name="grammar"></a>Gramatyka

*ASM — blok*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__asm`***instrukcja Assembly* **`;`** <sub>wybór</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__asm {`***instrukcja Assembly-list* **`}`** **`;`** <sub>wybór</sub>

*instrukcja Assembly-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrukcja Assembly* **`;`** <sub>wybór</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*instrukcja Assembly* **`;`** *instrukcja Assembly-list* **`;`** <sub>wybór</sub>

## <a name="remarks"></a>Uwagi

Jeśli jest używany bez nawiasów klamrowych, **`__asm`** słowo kluczowe oznacza, że pozostała część wiersza jest instrukcją języka asemblera. W przypadku użycia z nawiasami klamrowymi oznacza, że każdy wiersz między nawiasami jest instrukcją języka asemblera. W celu zapewnienia zgodności z poprzednimi wersjami, **`_asm`** jest synonimem dla **`__asm`** .

Ponieważ **`__asm`** słowo kluczowe jest separatorem instrukcji, można umieścić instrukcje zestawu w tym samym wierszu.

Przed dodaniem programu Visual Studio 2005, instrukcja

```cpp
__asm int 3
```

nie powoduje, że kod natywny został wygenerowany po skompilowaniu z **/CLR**; Kompilator przetłumaczy instrukcję do instrukcji break środowiska CLR.

`__asm int 3`teraz wynikiem jest generowanie kodu natywnego dla funkcji. Jeśli chcesz, aby funkcja powodowała punkt przerwania w kodzie i jeśli chcesz, aby ta funkcja była skompilowana do MSIL, użyj [__debugbreak](../../intrinsics/debugbreak.md).

W celu zapewnienia zgodności z poprzednimi wersjami, **`_asm`** jest synonimem, **`__asm`** Jeśli opcja kompilatora [/za \( wyłączone rozszerzenia językowe](../../build/reference/za-ze-disable-language-extensions.md) nie została określona.

## <a name="example"></a>Przykład

Poniższy fragment kodu jest prostym **`__asm`** blokiem ujętym w nawiasy klamrowe:

```cpp
__asm {
   mov al, 2
   mov dx, 0xD007
   out dx, al
}
```

Alternatywnie możesz umieścić **`__asm`** przed każdą instrukcją zestawu:

```cpp
__asm mov al, 2
__asm mov dx, 0xD007
__asm out dx, al
```

Ponieważ **`__asm`** słowo kluczowe jest separatorem instrukcji, można również umieścić instrukcje zestawu w tym samym wierszu:

```cpp
__asm mov al, 2   __asm mov dx, 0xD007   __asm out dx, al
```

Wszystkie trzy przykłady generują ten sam kod, ale pierwszy styl (otaczający **`__asm`** blok w nawiasach klamrowych) ma pewne zalety. Nawiasy klamrowe wyraźnie oddzielają kod zestawu od kodu C lub C++ i unikają niepotrzebnego powtórzenia **`__asm`** słowa kluczowego. Nawiasy klamrowe mogą również uniemożliwić niejasności. Jeśli chcesz umieścić instrukcję C lub C++ w tym samym wierszu co **`__asm`** blok, należy ująć blok w nawiasy klamrowe. Bez nawiasów klamrowych kompilator nie może stwierdzić, gdzie zakończył się kod zestawu i rozpoczyna instrukcje C lub C++. Na koniec, ponieważ tekst w nawiasach ma taki sam format jak zwykły tekst MASM, można łatwo wyciąć i wkleić tekst z istniejących plików źródłowych MASM.

W przeciwieństwie do nawiasów klamrowych w C i C++, nawiasy klamrowe otaczające **`__asm`** blok nie wpływają na zakres zmiennej. Bloki można zagnieżdżać **`__asm`** , ponieważ zagnieżdżenie nie ma wpływu na zakres zmiennej.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../../cpp/keywords-cpp.md)<br/>
[Asembler wbudowany](../../assembler/inline/inline-assembler.md)<br/>
