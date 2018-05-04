---
title: /Zc:alignedNew (c ++ 17 nadmiernie wyrównany alokacji) | Dokumentacja firmy Microsoft
ms.date: 02/28/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc:alignedNew
dev_langs:
- C++
helpviewer_keywords:
- /Zc:alignedNew
- Zc:alignedNew
- -Zc:alignedNew
author: corob-msft
ms.author: corob
ms.openlocfilehash: 5f9527d63a9843bd4df90520e5b4759126d72fe1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="zcalignednew-c17-over-aligned-allocation"></a>/Zc:alignedNew (c ++ 17 nadmiernie wyrównany alokacji)

Włączenie obsługi języka C ++ 17 nadmiernie wyrównane **nowe**, dynamicznej alokacji pamięci wyrównane na granicach większa niż wartość domyślna o rozmiarze maksymalnie wyrównany standardowej, **max\_Dopasuj\_t**.

## <a name="syntax"></a>Składnia

> **/Zc:alignedNew**[-]

## <a name="remarks"></a>Uwagi

Program Visual Studio wersja 15,5 cala pozwala kompilator i biblioteki obsługę języka C ++ 17 standardowe nadmiernie wyrównany dynamicznej alokacji pamięci. Gdy **/Zc:alignedNew** określono opcję dynamicznego przydziału `new Example;` szanuje wyrównanie *przykład* nawet jeśli jest większa niż `max_align_t`, największy wyrównania wymagany dla wszystkich typów podstawowych. Gdy wyrównanie przydzielonego typu jest nie więcej niż gwarantowane przez operator oryginalnego **nowe**, dostępne jako wartość wstępnie zdefiniowanego makra  **\_ \_STDCPP\_domyślne \_Nowy\_WYRÓWNANIE\_\_**, instrukcja `new Example;` powoduje wywołanie `::operator new(size_t)` tak jak w języku C ++ 14. Jeśli wyrównanie jest większa niż  **\_ \_STDCPP\_domyślne\_nowy\_WYRÓWNANIE\_\_**, implementacja zamian uzyskuje pamięć przy użyciu `::operator new(size_t, align_val_t)`. Podobnie, wywołuje usunięcia nadmiernie wyrównane typy `::operator delete(void*, align_val_t)` lub rozmiarze usunąć podpisu `::operator delete(void*, size_t, align_val_t)`.

**/Zc:alignedNew** opcja jest dostępna tylko podczas [/std:c ++ 17](std-specify-language-standard-version.md) lub [/std:c ++ najnowsze](std-specify-language-standard-version.md) jest włączona. W obszarze **/std:c ++ 17** lub **/std:c ++ najnowsze**, **/Zc:alignedNew** jest domyślnie włączone są zgodne z normą ISO w standardzie C ++ 17. Jeśli tylko przyczyny zaimplementować operator **nowe** i **usunąć** służy do obsługi nadmiernego wyrównany alokacji nie należy tego kodu w trybie C ++ 17. Aby wyłączyć tę opcję i przywrócić C ++ 14 zachowania **nowe** i **usunąć** podczas **/std::c ++ 17** lub **/std:c ++ najnowsze** jest określony, Określ **/Zc:alignedNew-**. W przypadku zastosowania operatora **nowe** i **usunąć** , ale nie jest jeszcze gotowa do zaimplementowania nadmiernie wyrównany operator **nowe** i **usunąć** przeciążenia, które mają `align_val_t` parametru, użyj **/Zc:alignedNew-** opcję, aby uniemożliwić generowania kompilator i biblioteki standardowej wywołań nadmiernie wyrównany przeciążenia. [/ Ograniczająca-](permissive-standards-conformance.md) opcji nie zmienia domyślne ustawienie **/Zc:alignedNew**.

## <a name="example"></a>Przykład

W tym przykładzie pokazano sposób operator **nowe** and — operator **usunąć** zachowanie, gdy **/Zc:alignedNew** ustawiono opcję.

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

Te dane wyjściowe jest typowa dla 32-bitowych wersjach. Wskaźnik, które różnią się wartości oparte na którym aplikacja jest uruchomiona w pamięci.

```Output
unaligned new(4) = 009FD0D0
unaligned sized delete(009FD0D0, 4)
aligned new(256, 256) = 009FE800
aligned sized delete(009FE800, 256, 256)
```

Aby uzyskać informacje o problemach zgodność w programie Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** strony właściwości.

1. Modyfikowanie **dodatkowe opcje** właściwości, aby uwzględnić **/Zc:alignedNew** lub **/Zc:alignedNew-** , a następnie wybierz **OK**.

## <a name="see-also"></a>Zobacz także

[/Zc (Zgodność)](../../build/reference/zc-conformance.md)  
