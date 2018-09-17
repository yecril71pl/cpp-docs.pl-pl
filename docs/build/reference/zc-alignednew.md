---
title: '/ Zc: alignednew (c ++ 17 nadmiernie wyrównana alokacja) | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: aba188a69af0449dd05df4bff14567f79a72c068
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721438"
---
# <a name="zcalignednew-c17-over-aligned-allocation"></a>/ Zc: alignednew (c ++ 17 nadmiernie wyrównana alokacja)

Włącz obsługę standardu C ++ 17 nadmiernie wyrównanych **nowe**, dynamicznej alokacji pamięci wyrównane na granicach większa niż wartość domyślna o maksymalnym rozmiarze wyrównany standardowej, **max\_wyrównać\_t**.

## <a name="syntax"></a>Składnia

> **/ Zc: alignednew**[-]

## <a name="remarks"></a>Uwagi

Program Visual Studio w wersji 15.5 umożliwia kompilatora i obsługa bibliotek dla języka C ++ 17 standardowa nadmiernie wyrównanych dynamicznej alokacji pamięci. Gdy **/Zc: alignednew** opcja jest określona, dynamicznej alokacji, takie jak `new Example;` szanuje wyrównanie *przykład* nawet jeśli jest większa niż `max_align_t`, największemu wyrównaniu wymagane dla wszystkich typów podstawowych. Po nie więcej niż gwarantowane przez operatora, oryginalnym wyrównanie typu przydzielonego **nowe**, która jest dostępna jako wartość wstępnie zdefiniowane makro  **\_ \_STDCPP\_domyślne \_NEW\_WYRÓWNANIE\_\_**, instrukcja `new Example;` powoduje wywołanie `::operator new(size_t)` tak jak w języku C ++ 14. Gdy wyrównania jest większa niż  **\_ \_STDCPP\_domyślne\_nowy\_WYRÓWNANIE\_\_**, implementacja zamiast tego uzyskuje pamięć przy użyciu `::operator new(size_t, align_val_t)`. Podobnie, wywołuje usuwania typów nadmiernie wyrównanych `::operator delete(void*, align_val_t)` lub wielkości Usuń podpis `::operator delete(void*, size_t, align_val_t)`.

**/Zc: alignednew** opcja jest dostępna tylko podczas [/STD: c ++ 17](std-specify-language-standard-version.md) lub [/STD: c ++ najnowsze](std-specify-language-standard-version.md) jest włączona. W obszarze **/STD: c ++ 17** lub **/STD: c ++ najnowsze**, **/Zc: alignednew** jest domyślnie włączona, aby były zgodne z normą ISO w standardzie C ++ 17. Jeśli tylko przyczyny implementuje operatora **nowe** i **Usuń** służy do obsługi alokacje nadmiernie wyrównanych, już nie potrzebujesz tego kodu w trybie C ++ 17. Aby wyłączyć tę opcję i powrócić do języka C ++ 14 zachowanie **nowe** i **Usuń** podczas **/std::c ++ 17** lub **/STD: c ++ najnowsze** jest określony, Określ **/Zc:alignedNew-**. W przypadku zastosowania operatora **nowe** i **Usuń** , ale nie jest jeszcze gotowa do zaimplementowania nadmiernie wyrównanych operator **nowe** i **Usuń** przeciążenia, które mają `align_val_t` parametru, użyj **/Zc:alignedNew-** opcję, aby uniemożliwić wygenerowanie przez kompilator i standardową bibliotekę wywołania przeciążenia nadmiernie wyrównana. [/ Permissive-](permissive-standards-conformance.md) opcja nie powoduje zmiany domyślne ustawienie **/Zc: alignednew**.

## <a name="example"></a>Przykład

Ten przykład pokazuje, jak operator **nowe** i operator **Usuń** zachowywać się, gdy **/Zc: alignednew** ustawiono opcję.

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

Te dane wyjściowe są typowe dla 32-bitowych kompilacji. Wskaźnik, które różnią się w wartości na podstawie której działa Twoja aplikacja w pamięci.

```Output
unaligned new(4) = 009FD0D0
unaligned sized delete(009FD0D0, 4)
aligned new(256, 256) = 009FE800
aligned sized delete(009FE800, 256, 256)
```

Aby uzyskać informacje na temat problemów ze zgodnością w języku Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** stronę właściwości.

1. Modyfikowanie **dodatkowe opcje** właściwości do uwzględnienia **/Zc: alignednew** lub **/Zc:alignedNew-** , a następnie wybierz **OK**.

## <a name="see-also"></a>Zobacz także

[/Zc (Zgodność)](../../build/reference/zc-conformance.md)
