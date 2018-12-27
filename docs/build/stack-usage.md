---
title: x64 stosu użycia
ms.date: 12/17/2018
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
ms.openlocfilehash: 3318a3512f83e242496454ffa2dc4aa8d26e1fc3
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53627322"
---
# <a name="x64-stack-usage"></a>x64 stosu użycia

Cała pamięć poza bieżący adres RSP jest uważana za volatile: Ta pamięć może spowodować zastąpienie systemu operacyjnego lub debugera, podczas sesji debugowania użytkownika lub program obsługi przerwania. W efekcie RSP musi zawsze być ustawiona przed podjęciem próby odczytu lub zapisu wartości do ramki stosu.

W tej sekcji omówiono alokację miejsca na stosie dla zmiennych lokalnych i **alloca** wewnętrzne.

## <a name="stack-allocation"></a>Alokacja stosu

Prologu funkcji jest odpowiedzialny za przydzielanie miejsca na stosie dla zmiennych lokalnych, zapisane rejestrów, stos parametry i parametry rejestru.

W obszarze parametrów jest zawsze w dolnej części stosu (nawet wtedy, gdy `alloca` jest używany), dzięki czemu zawsze będzie sąsiadujące adres zwrotny podczas każde wywołanie funkcji. Zawiera on co najmniej cztery wpisy, ale zawsze wystarczającej ilości miejsca dla wszystkich parametrów wymaganych przez dowolną funkcję, która może zostać wywołana. Należy zauważyć, że dla parametrów rejestru miejsca jest zawsze przydzielana, nawet wtedy, gdy same parametry nigdy nie są umieszczone na stosie; / / wywoływany ma żadnej gwarancji, że miejsca przydzielonego dla jego parametrów. Adresy domowe są wymagane dla argumentów rejestru, więc ciągły obszar jest dostępna w przypadku, gdy wywołana funkcja musi przyjąć adresu listy argumentów (va_list) lub poszczególnych argumentu. Ten obszar zawiera również wygodne miejsce do zapisania rejestru argumentów podczas wykonywania thunk i opcję debugowania (na przykład, ułatwia argumenty znaleźć podczas debugowania, jeśli są one przechowywane na adresy domowe w kodzie prologu). Nawet wtedy, gdy wywołana funkcja ma następujące parametry mniej niż 4, te lokalizacje stosu 4 skutecznie własnością wywołanej funkcji i może być używany przez funkcję o nazwie do innych celów, oprócz zapisywanie parametru wartości rejestru.  Ten sposób obiekt wywołujący może nie zostać zapisana informacje w tym regionie stosu w wywołaniu funkcji.

Jeśli miejsce jest przydzielany dynamicznie (`alloca`) w przypadku funkcji nieulotnej rejestru musi być następnie użyta jako wskaźnik ramki do oznaczania base stałej części stosu i rejestru musi być zapisany i inicjowana w prologu. Należy pamiętać, że w przypadku `alloca` jest używany, wywołania do tej samej / / wywoływany z tego samego obiektu wywołującego może mieć różne adresy domowe ich parametrów rejestru.

Stos zostanie zachowany 16-bajtowy wyrównane, z wyjątkiem w prologu (na przykład po zostanie przypisany adres zwrotny) i z wyjątkiem wskazanych w [typy funkcji](#function-types) dla klasy funkcje ramki.

Poniżej przedstawiono, że przykładowy układ stosu, w którym wywołania funkcji element niebędący liściem funkcji prologu funkcji B. A ma już przydzielone miejsce dla wszystkich parametrów rejestru i stosu wymagane przez B na dole stosu. Wywołanie wypycha adres zwrotny i prologu B przydziela miejsce dla jego zmiennych lokalnych, nieulotnej rejestrów i miejsce wymagane do jej do wywołania funkcji. Jeśli B używa `alloca`, miejsce jest przydzielane między lokalnego rejestru zmiennej/nieulotnej Zapisz obszar i obszaru stosu parametru.

![Przykład konwersji AMD](../build/media/vcamd_conv_ex_5.png "AMD przykład konwersji")

Gdy funkcja B wywołuje inną funkcję, adres zwrotny jest wypychane bezpośrednio pod adres domowy dla RCX.

## <a name="dynamic-parameter-stack-area-construction"></a>Konstrukcja obszaru stosu parametru dynamicznego

Jeśli jest używany wskaźnik ramki, istnieje możliwość umożliwia dynamiczne tworzenie obszaru stosu parametru. Nie jest to aktualnie wykonywane w x64 kompilatora.

## <a name="function-types"></a>Typy funkcji

Istnieją dwa typy funkcji. Nosi nazwę funkcji, która wymaga ramkę stosu *ramki funkcja*. Funkcja, która nie wymaga ramka stosu jest wywoływana *liści funkcja*.

Funkcja ramki jest funkcją, która przydziela miejsce stosu, wywołuje inne funkcje, zapisuje nieulotnej rejestrów lub korzysta z obsługi wyjątków. Wymaga to również wpisu tabeli funkcji. Funkcja ramki wymaga prologu i epilogu. Funkcja ramki mogą dynamicznie przydzielać obszar stosu i mogą stosować wskaźnik ramki. Funkcja ramki ma pełnego zestawu funkcji to wywołanie standardowa swojej dyspozycji.

Jeśli funkcja ramki nie wywołuje inną funkcję, wówczas nie jest wymagane do wyrównania stosu (do których odwołuje się w sekcji [alokacji stosu](#stack-allocation)).

Funkcja liścia to taki, który nie wymaga wpisu tabeli funkcji. Go nie zmieniać nieulotnej rejestrów, w tym RSP, co oznacza, że nie wywołaniem dowolnej funkcji i przydzielenie miejsca na stosie. Może on być pozostaw niewyrównanych stosu podczas wykonywania.

## <a name="malloc-alignment"></a>malloc, wyrównanie

[malloc](../c-runtime-library/reference/malloc.md) gwarancję zwracania pamięci, który jest odpowiednio wyrównana do przechowywania dowolnego obiektu, który ma podstawowe wyrównanie i który może zmieścić ilość przydzielonej pamięci. A *podstawowe wyrównanie* jest wyrównanie, które jest mniejsze niż lub równe największemu wyrównaniu, która jest obsługiwana przez implementację bez specyfikacji wyrównania. (W programie Visual C++ to wyrównania, która jest wymagana dla `double`, lub 8 bajtów. W kodzie, który jest przeznaczony dla platform 64-bitowy to 16 bajtów.) Na przykład alokacja Czterobajtowa byłaby wyrównana do granicy, który obsługuje dowolny obiekt obiekty czterobajtowe lub mniejsze.

Visual C++ pozwala na typy, które mają *rozszerzone wyrównanie*, które są również nazywane *nadmiernie wyrównanych* typów. Na przykład typy SSE [__m128](../cpp/m128.md) i `__m256`oraz typy, które są zadeklarowane za pomocą `__declspec(align( n ))` gdzie `n` jest większa niż 8, mają rozszerzone wyrównanie. Wyrównanie pamięci na granicy, która jest odpowiednia dla obiektu, który wymaga rozszerzonego wyrównania, nie jest zagwarantowana przez `malloc`. Aby przydzielić pamięć dla typów nadmiernie wyrównanych, użyj [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) i pokrewnych funkcji.

## <a name="alloca"></a>alloca

[_alloca](../c-runtime-library/reference/alloca.md) musi być 16-bajtowy wyrównany, a ponadto trzeba użyć wskaźnika ramki.

Stos, który jest przydzielony musi zawierać miejsca po nim dla parametrów funkcji następnie wywoływana, zgodnie z opisem w [alokacji stosu](#stack-allocation).

## <a name="see-also"></a>Zobacz też

[x64 konwencje kodowania](../build/x64-software-conventions.md)<br/>
[align](../cpp/align-cpp.md)<br/>
[__declspec](../cpp/declspec.md)