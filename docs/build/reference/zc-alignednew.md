---
title: /Zc:alignedNew (Nadmiernie wyrównana alokacja C++17)
ms.date: 05/18/2019
f1_keywords:
- /Zc:alignedNew
helpviewer_keywords:
- /Zc:alignedNew
- Zc:alignedNew
- -Zc:alignedNew
ms.openlocfilehash: f036c2d7bc4619685d2763702f447476e8e1a1e4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217197"
---
# <a name="zcalignednew-c17-over-aligned-allocation"></a>/Zc:alignedNew (Nadmiernie wyrównana alokacja C++17)

Włącz obsługę w porównaniu z trybem wyrównania w języku C++ 17 **`new`** , czyli alokację pamięci dynamicznej wyrównanej do granic większej niż domyślna dla standardowego typu wyrównanego do rozmiaru, **maks \_ \_ **.

## <a name="syntax"></a>Składnia

> **/Zc: alignedNew** \[ -]

## <a name="remarks"></a>Uwagi

Kompilator i Biblioteka MSVC obsługują standardową alokację pamięci w języku C++ 17. Gdy jest określona opcja **/Zc: alignedNew** , dynamiczna alokacja, taka jak odnosi `new Example;` się do wyrównania *przykładu* , nawet jeśli jest większa niż `max_align_t` , największe wyrównanie wymagane dla każdego typu podstawowego. Gdy wyrównanie przydzielonego typu nie jest więcej niż wyrównanie gwarantowane przez oryginalny operator **`new`** , dostępne jako wartość wstępnie zdefiniowanego makra ** \_ \_ STDCPP \_ domyślne ustawienie \_ \_ \_ \_ wyrównania**, instrukcja `new Example;` powoduje wywołanie `::operator new(size_t)` tak jak w języku c++ 14. Gdy wyrównanie jest większe niż ** \_ \_ \_ domyślne \_ nowe \_ \_ \_ wyrównanie STDCPP**, implementacja zamiast tego uzyskuje pamięć przy użyciu `::operator new(size_t, align_val_t)` . Analogicznie, usuwanie nadmiernie wyrównanych typów wywołuje `::operator delete(void*, align_val_t)` lub usuwa sygnaturę usuwania `::operator delete(void*, size_t, align_val_t)` .

Opcja **/Zc: alignedNew** jest dostępna tylko wtedy, gdy [/std: c++ 17](std-specify-language-standard-version.md) lub [/std: c + + Najnowsza](std-specify-language-standard-version.md) jest włączona. W obszarze **/std: c++ 17** lub **/std: c + + Najnowsza**, **/Zc: alignedNew** jest włączona domyślnie, aby była zgodna ze standardem ISO c++ 17. Jeśli jedyną przyczyną jest implementacja operatora **`new`** i **`delete`** jest obsługa nadmiernych przydziałów, ten kod może nie być już potrzebny w trybie c++ 17. Aby wyłączyć tę opcję i przywrócić zachowanie języka C++ 14 **`new`** i w **`delete`** przypadku korzystania z **/std:: c++ 17** lub **/std: C + + Najnowsza**, określ **/Zc: alignedNew-**. W przypadku zaimplementowania operatora **`new`** i **`delete`** ale nie jest gotowy do implementacji operatora nadmiernie wyrównanych **`new`** i **`delete`** przeciążeń, które mają ten `align_val_t` parametr, należy użyć opcji **/Zc: alignedNew-** , aby zapobiec generowaniu wywołań do nadmiernie wyrównanych przeciążeń. Opcja [/permissive-](permissive-standards-conformance.md) nie zmienia domyślnego ustawienia **/Zc: alignedNew**.

Obsługa **/Zc: alignedNew** jest dostępna w programie Visual Studio 2017 w wersji 15,5.

## <a name="example"></a>Przykład

Ten przykład pokazuje, jak **`new`** działa operator i operator **`delete`** po ustawieniu opcji **/Zc: alignedNew** .

```cpp
// alignedNew.cpp
// Compile by using: cl /EHsc /std:c++17 /W4 alignedNew.cpp
#include <iostream>
#include <malloc.h>
#include <new>

// "old" unaligned overloads
void* operator new(std::size_t size) {
    auto ptr = malloc(size);
    std::cout << "unaligned new(" << size << ") = " << ptr << '\n';
    return ptr ? ptr : throw std::bad_alloc{};
}

void operator delete(void* ptr, std::size_t size) {
    std::cout << "unaligned sized delete(" << ptr << ", " << size << ")\n";
    free(ptr);
}

void operator delete(void* ptr) {
    std::cout << "unaligned unsized delete(" << ptr << ")\n";
    free(ptr);
}

// "new" over-aligned overloads
void* operator new(std::size_t size, std::align_val_t align) {
    auto ptr = _aligned_malloc(size, static_cast<std::size_t>(align));
    std::cout << "aligned new(" << size << ", " <<
        static_cast<std::size_t>(align) << ") = " << ptr << '\n';
    return ptr ? ptr : throw std::bad_alloc{};
}

void operator delete(void* ptr, std::size_t size, std::align_val_t align) {
    std::cout << "aligned sized delete(" << ptr << ", " << size <<
        ", " << static_cast<std::size_t>(align) << ")\n";
    _aligned_free(ptr);
}

void operator delete(void* ptr, std::align_val_t align) {
    std::cout << "aligned unsized delete(" << ptr <<
        ", " << static_cast<std::size_t>(align) << ")\n";
    _aligned_free(ptr);
}

struct alignas(256) OverAligned {}; // warning C4324, structure is padded

int main() {
    delete new int;
    delete new OverAligned;
}
```

Te dane wyjściowe są typowe dla kompilacji 32-bitowych. Wartości wskaźnika różnią się w zależności od tego, gdzie aplikacja jest uruchamiana w pamięci.

```Output
unaligned new(4) = 009FD0D0
unaligned sized delete(009FD0D0, 4)
aligned new(256, 256) = 009FE800
aligned sized delete(009FE800, 256, 256)
```

Aby uzyskać informacje o problemach ze zgodnością w Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Configuration Properties**  >  stronę właściwości konfiguracja wiersza polecenia**C/C++**  >  **Command Line** .

1. Zmodyfikuj właściwość **Opcje dodatkowe** , aby uwzględnić **/Zc: alignedNew** lub **/Zc: alignedNew-** , a następnie wybierz **przycisk OK**.

## <a name="see-also"></a>Zobacz także

[/Zc (Zgodność)](zc-conformance.md)
