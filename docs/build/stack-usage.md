---
title: Użycie stosu x64
ms.date: 12/17/2018
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
ms.openlocfilehash: b598c33fbdd56630ca3e5ef0da551f38a73baa26
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335532"
---
# <a name="x64-stack-usage"></a>Użycie stosu x64

Cała pamięć poza bieżący adres RSP jest uważany za nietrwałe: System operacyjny lub debuger, może zastąpić tę pamięć podczas sesji debugowania użytkownika lub obsługi przerwań. W związku z tym RSP musi być zawsze ustawiona przed próbą odczytu lub zapisu wartości do ramki stosu.

W tej sekcji omówiono alokacji miejsca na stosie dla zmiennych lokalnych i **alloca** wewnętrzne.

## <a name="stack-allocation"></a>Alokacja stosu

Prolog funkcji jest odpowiedzialny za przydzielanie miejsca na stos dla zmiennych lokalnych, zapisanych rejestrów, parametrów stosu i parametrów rejestru.

Obszar parametru jest zawsze w dolnej `alloca` części stosu (nawet jeśli jest używany), tak, że zawsze będzie przylegał do adresu zwrotnego podczas wywołania funkcji. Zawiera co najmniej cztery wpisy, ale zawsze wystarczająco dużo miejsca, aby pomieścić wszystkie parametry wymagane przez dowolną funkcję, która może być wywoływana. Należy zauważyć, że miejsce jest zawsze przydzielane dla parametrów rejestru, nawet jeśli same parametry nigdy nie są homed do stosu; wywoływany jest gwarantowana, że miejsce zostało przydzielone dla wszystkich jego parametrów. Adresy macierzyste są wymagane dla argumentów rejestru, więc ciągły obszar jest dostępny w przypadku, gdy wywoływana funkcja musi przyjąć adres listy argumentów (va_list) lub indywidualny argument. Ten obszar zapewnia również wygodne miejsce do zapisywania argumentów rejestru podczas wykonywania thunk i jako opcja debugowania (na przykład sprawia, że argumenty są łatwe do znalezienia podczas debugowania, jeśli są one przechowywane pod adresami domowymi w kodzie prologu). Nawet jeśli wywołana funkcja ma mniej niż 4 parametry, te 4 lokalizacje stosu są skutecznie własnością wywoływaną funkcję i mogą być używane przez wywołaną funkcję do innych celów oprócz zapisywania wartości rejestru parametrów.  W związku z tym wywołujący nie może zapisać informacje w tym regionie stosu w wywołaniu funkcji.

Jeśli miejsce jest dynamicznie przydzielane (`alloca`) w funkcji, rejestr nieulotny musi być używany jako wskaźnik ramki, aby oznaczyć podstawę stałej części stosu, a rejestr musi zostać zapisany i zainicjowany w prologu. Należy zauważyć, że gdy `alloca` jest używany, wywołania tego samego wywoływacza z tego samego obiektu wywołującego może mieć różne adresy domowe dla ich parametrów rejestru.

Stos będzie zawsze utrzymywane 16-bajtowy wyrównane, z wyjątkiem w prologu (na przykład po adres zwrotny jest wypychany) i z wyjątkiem przypadków wskazanych w [typy funkcji](#function-types) dla określonej klasy funkcji ramki.

Poniżej przedstawiono przykład układu stosu, gdzie funkcja A wywołuje funkcję b. Prolog funkcji A ma już przydzielone miejsce dla wszystkich parametrów rejestru i stosu wymaganych przez B w dolnej części stosu. Wywołanie wypycha adres zwrotny, a prolog B przydziela miejsce dla swoich zmiennych lokalnych, rejestrów nieulotnych i miejsca potrzebnego do wywoływania funkcji. Jeśli B `alloca`używa , miejsce jest przydzielane między zmienną lokalną/nieulotny rejestr zapisz obszar i obszar stosu parametrów.

![Przykład konwersji AMD](../build/media/vcamd_conv_ex_5.png "Przykład konwersji AMD")

Gdy funkcja B wywołuje inną funkcję, adres zwrotny jest wypychany tuż poniżej adresu domowego dla RCX.

## <a name="dynamic-parameter-stack-area-construction"></a>Konstrukcja obszaru stosu parametrów dynamicznych

Jeśli używany jest wskaźnik ramki, istnieje opcja dynamicznego tworzenia obszaru stosu parametrów. Obecnie nie jest to wykonywane w kompilatorze x64.

## <a name="function-types"></a>Typy funkcji

Istnieją w zasadzie dwa rodzaje funkcji. Funkcja wymagająca ramki stosu jest nazywana *funkcją ramki*. Funkcja, która nie wymaga ramki stosu, jest nazywana *funkcją liścia*.

Funkcja ramki jest funkcją, która przydziela miejsce na stosie, wywołuje inne funkcje, zapisuje rejestry nieulotne lub używa obsługi wyjątków. Wymaga również wpisu tabeli funkcji. Funkcja ramki wymaga prologu i epilogu. Funkcja ramki może dynamicznie przydzielać miejsce na stosie i może stosować wskaźnik ramki. Funkcja ramki ma pełne możliwości tego standardu wywołującego do swojej dyspozycji.

Jeśli funkcja ramki nie wywoła innej funkcji, nie jest wymagane wyrównywanie stosu (odwołuje się do [alokacji stosu](#stack-allocation)sekcji).

Funkcja liścia to taka, która nie wymaga wpisu tabeli funkcji. Nie można wprowadzać zmian w żadnych rejestrach nieulotnych, w tym RSP, co oznacza, że nie można wywołać żadnych funkcji ani przydzielić miejsca na stosie. Dozwolone jest pozostawienie stosu niewyrównane podczas wykonywania.

## <a name="malloc-alignment"></a>wyrównanie malloc

[malloc](../c-runtime-library/reference/malloc.md) jest gwarantowane do zwrócenia pamięci, która jest odpowiednio wyrównane do przechowywania dowolnego obiektu, który ma podstawowe wyrównanie i które mogą zmieścić się w ilości pamięci, która jest przydzielona. *Wyrównanie podstawowe* jest wyrównanie, które jest mniej niż lub równa największego wyrównania, który jest obsługiwany przez implementację bez specyfikacji wyrównania. (W języku Visual C++jest to wyrównanie wymagane `double`dla , lub 8 bajtów. W kodzie przeznaczonym dla platform 64-bitowych jest to 16 bajtów.) Na przykład alokacja czterech bajtów zostanie wyrównana do granicy, która obsługuje dowolny obiekt cztero bajtowy lub mniejszy.

Visual C++ zezwala na typy, które mają *wyrównanie rozszerzone*, które są również *nazywane typami przerekułkowanymi.* Na przykład typy [__m128](../cpp/m128.md) SSE __m128 `__m256`i , i typy, które są zadeklarowane przy użyciu `__declspec(align( n ))` gdzie `n` jest większa niż 8, mają rozszerzone wyrównanie. Wyrównanie pamięci na granicy, która jest odpowiednia dla obiektu, `malloc`który wymaga rozszerzonego wyrównania nie jest gwarantowana przez program . Aby przydzielić pamięć dla typów przerekłajnych, należy użyć [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) i powiązanych funkcji.

## <a name="alloca"></a>alloca

[_alloca](../c-runtime-library/reference/alloca.md) musi być wyrównany o 16 bajtów i dodatkowo wymagany do użycia wskaźnika ramki.

Stos, który jest przydzielany musi zawierać miejsce po nim dla parametrów później nazywanych funkcji, jak omówiono w [alokacji stosu](#stack-allocation).

## <a name="see-also"></a>Zobacz też

[Konwencje kodowania x64](../build/x64-software-conventions.md)<br/>
[Wyrównaj](../cpp/align-cpp.md)<br/>
[__declspec](../cpp/declspec.md)
