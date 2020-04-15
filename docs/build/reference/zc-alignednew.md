---
title: /Zc:alignedNew (Nadmiernie wyrównana alokacja C++17)
ms.date: 05/18/2019
f1_keywords:
- /Zc:alignedNew
helpviewer_keywords:
- /Zc:alignedNew
- Zc:alignedNew
- -Zc:alignedNew
ms.openlocfilehash: 041f62bbbf5f7a2750960d21d1534cf6daf4b874
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335683"
---
# <a name="zcalignednew-c17-over-aligned-allocation"></a>/Zc:alignedNew (Nadmiernie wyrównana alokacja C++17)

Włącz obsługę c++17 przerekcełowanej **nowej,** dynamicznej alokacji pamięci wyrównanej do granic większych niż domyślny dla standardowego typu wyrównanego o maksymalnym rozmiarze, **maksymalnie\_wyrównać\_t**.

## <a name="syntax"></a>Składnia

> **/Zc:alignedNew**\[-]

## <a name="remarks"></a>Uwagi

Kompilator MSVC i biblioteka obsługują standardową alokację pamięci dynamicznej w języku C++17. Po określeniu **opcji /Zc:alignedNew** alokacja `new Example;` dynamiczna, taka jak wyrównanie *example,* nawet wtedy, gdy jest większa niż `max_align_t`, największe wyrównanie wymagane dla dowolnego typu podstawowego. Gdy wyrównanie przydzielonego typu jest nie więcej niż wyrównanie gwarantowane przez oryginalnego operatora **nowy,** dostępne jako wartość wstępnie `new Example;` zdefiniowanego makra ** \_ \_\_STDCPP DEFAULT\_NEW\_ALIGNMENT\_**, instrukcja powoduje `::operator new(size_t)` wywołanie, jak to miało miejsce w C ++ 14. Gdy wyrównanie jest większe niż `::operator new(size_t, align_val_t)` ** \_ \_WYRÓWNANIE DOMYŚLNE\_\_STDCPP,\_\_** implementacja zamiast tego uzyskuje pamięć za pomocą programu . Podobnie, usunięcie typów przerekłokowanych `::operator delete(void*, align_val_t)` wywołuje lub rozmiar `::operator delete(void*, size_t, align_val_t)`delete podpisu .

Opcja **/Zc:alignedNew** jest dostępna tylko wtedy, gdy włączona jest [opcja /std:c++17](std-specify-language-standard-version.md) lub [/std:c++latest.](std-specify-language-standard-version.md) W **obszarze /std:c++17** lub **/std:c++latest** **,/Zc:alignedNew** jest domyślnie włączona, aby była zgodna ze standardem ISO C++17. Jeśli jedynym powodem implementowania operatora **nowy** i **usunąć** jest obsługa alokacji przerekranowane, może nie być już potrzebny ten kod w trybie C++17. Aby wyłączyć tę opcję i przywrócić zachowanie c++14 **nowego** i **usunąć** podczas korzystania **z /std::c++17** lub **/std:c++latest**, specify **/Zc:alignnew-**. Jeśli zaimplementujesz operator **nowy** i **usunąć,** ale nie jesteś gotowy do zaimplementowania operatora przerównane **nowe** i **usunąć** przeciążenia, które mają `align_val_t` parametr, należy użyć **/Zc:alignedNew-** opcja, aby zapobiec kompilator i biblioteka standardowa z generowania wywołań przerekroniowanych przeciążeń. Opcja [/permissive-](permissive-standards-conformance.md) nie zmienia domyślnego ustawienia **/Zc:alignNew**.

Obsługa **/Zc:alignedNew** jest dostępna począwszy od programu Visual Studio 2017 w wersji 15.5.

## <a name="example"></a>Przykład

W tym przykładzie pokazano, jak operator **nowy** i **usunięcie** operatora zachowują się po ustawieniu opcji **/Zc:alignedNew.**

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

To dane wyjściowe są typowe dla kompilacji 32-bitowych. Wartości wskaźnika różnią się w zależności od tego, gdzie aplikacja działa w pamięci.

```Output
unaligned new(4) = 009FD0D0
unaligned sized delete(009FD0D0, 4)
aligned new(256, 256) = 009FE800
aligned sized delete(009FE800, 256, 256)
```

Aby uzyskać informacje na temat problemów z zgodnością w programie Visual C++, zobacz [Niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **Strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora języka C++ i właściwości kompilacji w programie Visual Studio.](../working-with-project-properties.md)

1. Wybierz stronę właściwości**wiersza polecenia** **Właściwości** > konfiguracji**C/C++.** > 

1. Zmodyfikuj właściwość **Opcje dodatkowe,** aby uwzględnić **/Zc:alignnew** lub **/Zc:alignedNew-** a następnie wybierz **przycisk OK**.

## <a name="see-also"></a>Zobacz też

[/Zc (Zgodność)](zc-conformance.md)
