---
title: Użycie stosu x64
ms.date: 12/17/2018
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
ms.openlocfilehash: b1b1e0a8c30d5e24e81372912d5c488efce14841
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218939"
---
# <a name="x64-stack-usage"></a>Użycie stosu x64

Cała pamięć poza bieżącym adresem RSP jest uważana za nietrwałą: system operacyjny lub debuger, może zastąpić tę pamięć podczas sesji debugowania użytkownika lub programu obsługi przerwań. W ten sposób żądanie RSP musi być zawsze ustawione przed próbą odczytu lub zapisu wartości w ramce stosu.

W tej sekcji omówiono przydzielanie przestrzeni stosu dla zmiennych lokalnych i wewnętrznej **alokacji** przydziału.

## <a name="stack-allocation"></a>Alokacja stosu

Prolog funkcji jest odpowiedzialny za przydzielanie przestrzeni stosu dla zmiennych lokalnych, zapisanych rejestrów, parametrów stosu i parametrów rejestru.

Obszar parametru zawsze znajduje się w dolnej części stosu (nawet jeśli `alloca` jest używany), tak aby zawsze przylegał do adresu zwrotnego w trakcie wywołania funkcji. Zawiera co najmniej cztery wpisy, ale zawsze ma wystarczającą ilość miejsca do przechowywania wszystkich parametrów wymaganych przez każdą funkcję, która może być wywoływana. Należy zauważyć, że spacja jest zawsze przypisana do parametrów rejestru, nawet jeśli same parametry nigdy nie są umieszczone na stosie. wywoływany jest gwarantowanie, że miejsce zostało przydzieloną dla wszystkich jego parametrów. Adresy domowe są wymagane dla argumentów rejestru, aby obszar ciągły był dostępny w przypadku, gdy wywoływana funkcja musi przyjmować adres listy argumentów (va_list) lub pojedynczy argument. Ten obszar zapewnia również wygodne miejsce do zapisywania argumentów rejestru podczas wykonywania thunk oraz jako opcję debugowania (na przykład ułatwia wyszukiwanie argumentów podczas debugowania, jeśli są one przechowywane na ich adresach domowych w kodzie prologu). Nawet jeśli wywołana funkcja ma mniej niż 4 parametry, te 4 lokalizacje stosu są efektywnie własnością wywoływanej funkcji i mogą być używane przez wywołana funkcja do innych celów oprócz zapisywania wartości rejestru parametrów.  W rezultacie obiekt wywołujący nie może zapisywać informacji w tym regionie stosu w wywołaniu funkcji.

Jeśli miejsce jest przydzielane dynamicznie ( `alloca` ) w funkcji, należy użyć nietrwałego rejestru jako wskaźnika ramki, aby oznaczyć podstawę stałej części stosu, a rejestr musi być zapisany i zainicjowany w prologu. Należy pamiętać, że gdy `alloca` jest używany, wywołania do tego samego elementu wywoływanego z tego samego obiektu wywołującego mogą mieć różne adresy główne dla parametrów rejestru.

Stos będzie zawsze utrzymywany przez 16-bajtowe wyrównanie, z wyjątkiem prologu (na przykład po wypchnięciu adresu zwrotnego), z wyjątkiem przypadków wskazanych w [typach funkcji](#function-types) dla określonej klasy funkcji ramek.

Poniżej znajduje się przykład układu stosu, gdzie funkcja A wywołuje funkcję typu innego niż liść B. funkcja prologu jest już przydzielone miejsce dla wszystkich parametrów rejestru i stosu wymaganych przez B w dolnej części stosu. Wywołanie wypchnięcie adresu zwrotnego i prologu B przydziela miejsce dla jego zmiennych lokalnych, rejestrów nietrwałych oraz miejsca wymaganego do wywołania funkcji. Jeśli B używa `alloca` , miejsce jest przydzielono między zmienną lokalną/nielotny obszar zapisywania i obszarem stosu parametrów.

![Przykład konwersji AMD](../build/media/vcamd_conv_ex_5.png "Przykład konwersji AMD")

Gdy funkcja B wywołuje kolejną funkcję, adres zwrotny jest wypychany tuż poniżej adresu domowego dla RCX.

## <a name="dynamic-parameter-stack-area-construction"></a>Konstruowanie obszaru stosu parametrów dynamicznych

Jeśli jest używany wskaźnik ramki, istnieje możliwość dynamicznego tworzenia obszaru stosu parametrów. Nie jest to obecnie wykonywane w kompilatorze x64.

## <a name="function-types"></a>Typy funkcji

Istnieją zasadniczo dwa typy funkcji. Funkcja wymagająca ramki stosu jest nazywana *funkcją Frame*. Funkcja, która nie wymaga ramki stosu, jest nazywana *funkcją liścia*.

Funkcja Frame jest funkcją, która przydziela przestrzeń stosu, wywołuje inne funkcje, zapisuje niezalotne rejestry lub używa obsługi wyjątków. Wymaga również wpisu tabeli funkcji. Funkcja Frame wymaga prologu i epilogu. Funkcja Frame może dynamicznie przydzielić przestrzeń stosu i może korzystać ze wskaźnika ramki. Funkcja Frame ma pełne możliwości tego wywołania Standard.

Jeśli funkcja Frame nie wywołuje innej funkcji, nie jest wymagana do wyrównania stosu (przywoływanego w [alokacji stosu](#stack-allocation)sekcji).

Funkcja liścia to taka, która nie wymaga wpisu tabeli funkcji. Nie można wprowadzać zmian do żadnych nietrwałych rejestrów, w tym RSP, co oznacza, że nie może wywołać żadnych funkcji ani przydzielić przestrzeni stosu. Podczas wykonywania nie można pozostawić stosu w niewyrównanym czasie.

## <a name="malloc-alignment"></a>Wyrównanie malloc

Funkcja [malloc](../c-runtime-library/reference/malloc.md) gwarantuje, że pamięć jest odpowiednio wyrównana do przechowywania dowolnego obiektu, który ma podstawowe wyrównanie i który może pasować do ilości pamięci, która została przypisana. *Podstawowe wyrównanie* to wyrównanie, które jest mniejsze niż lub równe największemu wyrównaniu, które jest obsługiwane przez implementację bez określenia wyrównania. (W Visual C++ jest to wyrównanie wymagane dla **`double`** lub 8 bajtów. W kodzie, który jest przeznaczony dla platform 64-bitowych, wynosi 16 bajtów. Na przykład alokacja z czterema bajtami byłaby wyrównana na granicy, która obsługuje dowolny z czterech bajtów lub mniejszych obiektów.

Visual C++ zezwala na typy, które mają rozszerzone wyrównanie, które są również *znane jako* *przesunięte*typy. Na przykład typy SSE [__m128](../cpp/m128.md) i i `__m256` typy, które są zadeklarowane za pomocą `__declspec(align( n ))` gdzie `n` jest większy niż 8, mają rozszerzone wyrównanie. Wyrównanie pamięci na granicy, która jest odpowiednia dla obiektu, który wymaga rozszerzonego wyrównania, nie jest gwarantowane przez `malloc` . Aby przydzielić pamięć dla niewyrównanych typów, użyj [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) i powiązanych funkcji.

## <a name="alloca"></a>alloca

[_alloca](../c-runtime-library/reference/alloca.md) jest wymagany do 16-bajtowego wyrównania, a dodatkowo wymagane do użycia wskaźnika ramki.

Przydzielonego stosu musi zawierać miejsce po nim dla parametrów, które następnie nazywają funkcję, zgodnie z opisem w temacie [Alokacja stosu](#stack-allocation).

## <a name="see-also"></a>Zobacz także

[Konwencje kodowania x64](../build/x64-software-conventions.md)<br/>
[dostosowania](../cpp/align-cpp.md)<br/>
[__declspec](../cpp/declspec.md)
