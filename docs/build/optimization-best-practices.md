---
title: Najlepsze rozwiązania dotyczące optymalizacji
ms.date: 05/06/2019
helpviewer_keywords:
- C++, optimization
- optimization, best practices
ms.assetid: f3433148-7255-4ca6-8a4f-7c31aac88508
ms.openlocfilehash: 42178f8326def78f37bfcc905b96f37c7fc3affc
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220270"
---
# <a name="optimization-best-practices"></a>Najlepsze rozwiązania dotyczące optymalizacji

W tym dokumencie opisano najlepsze rozwiązania dotyczące optymalizacji C++ programy w programie Visual Studio.

## <a name="compiler-and-linker-options"></a>Kompilator i opcje konsolidatora

### <a name="profile-guided-optimization"></a>Optymalizacja sterowana profilem

Program Visual Studio obsługuje *optymalizacji sterowanej profilem* (PGO). Tego rodzaju optymalizacji używa danych profilu z wykonaniami szkolenia instrumentowanej wersji aplikacji do optymalizacji nowszych aplikacji. Przy użyciu PGO może zająć dużo czasu, dlatego nie może być coś, co każdy Deweloper używa, ale zaleca się używania optymalizacji PGO kompilacji ostatecznej wersji produktu. Aby uzyskać więcej informacji, zobacz [optymalizacje Profile-Guided](profile-guided-optimizations.md).

Ponadto *Optymalizacja Całoprogramowa* (również wie, jak łączonych kodów czasowych) i **/O1** i **/O2** optymalizacje zostały ulepszone. Ogólnie rzecz biorąc aplikacja skompilowana przy użyciu jednego z tych opcji krócej niż tej samej aplikacji skompilowanych za pomocą kompilatora wcześniejszych.

Aby uzyskać więcej informacji, zobacz [/GL (Optymalizacja Całoprogramowa)](reference/gl-whole-program-optimization.md) i [/O1, / O2 (Minimalizuj rozmiar, Maksymalizuj szybkość)](reference/o1-o2-minimize-size-maximize-speed.md).

### <a name="which-level-of-optimization-to-use"></a>Który poziom optymalizacji do użycia

Jeśli to możliwe ostateczna wersja kompilacji powinna być skompilowana przy użyciu optymalizacje z przewodnikiem profilu. Jeśli nie jest możliwe utworzenie przy użyciu PGO, czy ze względu na niewystarczające infrastruktury dla instrumentowanego kompilacji uruchomionych lub nie masz dostęp do scenariuszy, zalecamy tworzenie za pomocą optymalizacji całego programu.

**/Gy** przełącznik jest również bardzo przydatne. Generuje oddzielny COMDAT dla każdej funkcji, zapewniając większą elastyczność konsolidator, jeśli chodzi o usunięcie nieużywanych Comdat i COMDAT składanie. Jedyną wadą korzystania z interfejsu **/Gy** jest, że może to spowodować problemy podczas debugowania. W związku z tym ogólnie zaleca się jej używać. Aby uzyskać więcej informacji, zobacz [/Gy (Włącz łączenie poziomie funkcji)](reference/gy-enable-function-level-linking.md).

Łączenie w 64-bitowego środowiska, zaleca się używanie **/OPT: REF, ICF** — opcja konsolidatora i w środowisku 32-bitowych **/OPT: REF** jest zalecane. Aby uzyskać więcej informacji, zobacz [od (optymalizacje)](reference/opt-optimizations.md).

Zalecane jest również zdecydowanie Generuj symbole debugowania, nawet w przypadku kompilacji wydania zoptymalizowane. Nie ma wpływu na wygenerowany kod, a jego sprawia, że dużo łatwiejszy do debugowania aplikacji, jeśli muszą być.

### <a name="floating-point-switches"></a>Przełączniki zmiennoprzecinkowych

**/Op** — opcja kompilatora został usunięty i dodano następujące cztery opcje kompilatora dotyczących liczb zmiennoprzecinkowych optymalizacji punktu:

|||
|-|-|
|**/ FP: precise**|To jest określenia domyślnego zalecenia i powinny być używane w większości przypadków.|
|**Fast**|Zalecane, jeśli wydajności ma priorytetowe znaczenie, na przykład w grach. Spowoduje to zapewnić lepszą wydajność.|
|**/fp:strict**|Jeśli zalecana dokładne wyjątki zmiennoprzecinkowe i IEEE pożądane jest zachowanie. Spowoduje to najwolniejszy wydajności.|
|**/ FP: except [-]**|Mogą być używane w połączeniu z **/FP: strict** lub **/FP: precise**, ale nie **Fast**.|

Aby uzyskać więcej informacji, zobacz [/FP (określenie zachowania zmiennopozycyjna)](reference/fp-specify-floating-point-behavior.md).

## <a name="optimization-declspecs"></a>Declspecs optymalizacji

W tej sekcji omówimy dwie declspecs, używane w programach w celu poprawę wydajności: `__declspec(restrict)` i `__declspec(noalias)`.

`restrict` Declspec można stosować tylko do deklaracji funkcji, które zwracają wskaźnik, takich jak `__declspec(restrict) void *malloc(size_t size);`

`restrict` Declspec jest używany na funkcjach zwracających wskaźniki unaliased. To słowo kluczowe jest używany do wykonania biblioteki wykonawczej C `malloc` ponieważ nigdy nie zwróci wartość wskaźnika, który jest już używany w bieżącym programie (o ile nie zostanie robią coś, co jest niedozwolone, takich jak użycie pamięci po jego zwolnieniu).

`restrict` Declspec zapewnia kompilator dodatkowe informacje dotyczące wykonywania optymalizacje kompilatora. Jedną z kwestii najtrudniejsze dla kompilatora w celu określenia jest alias wskaźników, jakie inne wskaźniki i korzystając z tych informacji w znacznym stopniu pomaga kompilator.

Warto wskazywanie to obietnicę kompilator nie coś, co zweryfikuje kompilator. Jeśli program używa to `restrict` declspec niewłaściwie, program może spowodować nieprawidłowe zachowanie.

Aby uzyskać więcej informacji, zobacz [ograniczyć](../cpp/restrict.md).

`noalias` Declspec również jest stosowane tylko do funkcji i wskazuje, że funkcja jest częściową czystą funkcję. Częściowo czystą funkcję to taki, który odwołuje się lub modyfikuje zmienne lokalne, argumenty i elementów pierwszego poziomu pośrednich argumentów. Ten declspec jest obietnicą w kompilatorze i czy odwołuje się funkcja globals elementów pośrednich drugiego poziomu, argumenty wskaźnika, a następnie kompilator może wygenerować kod, dzieli aplikację.

Aby uzyskać więcej informacji, zobacz [noalias](../cpp/noalias.md).

## <a name="optimization-pragmas"></a>Optymalizacja pragm

Dostępne są także kilka pragmy przydatne dla ułatwienia optymalizacji kodu. Pierwszy z nich omówimy `#pragma optimize`:

```cpp
#pragma optimize("{opt-list}", on | off)
```

Ta dyrektywa pragma pozwala ustawić poziom optymalizacji danego na podstawie funkcji przez funkcję. Jest to idealne rozwiązanie dla rzadkich przypadkach, gdzie aplikacja ulegnie awarii podczas kompilowania z optymalizacją danej funkcji. Służy to do Wyłącz optymalizacje dla jednej funkcji:

```cpp
#pragma optimize("", off)
int myFunc() {...}
#pragma optimize("", on)
```

Aby uzyskać więcej informacji, zobacz [zoptymalizować](../preprocessor/optimize.md).

Wbudowanie jest jednym z najważniejszych optymalizacje, które kompilator wykonuje i tu omówione kilka pragm, ułatwiającą zmodyfikować to zachowanie.

`#pragma inline_recursion` jest przydatne do określenia, czy nie ma aplikacji, aby można było wbudowanego wywołanie cykliczne. Domyślnie jest wyłączona. Skrócona rekursji małych funkcji może ją włączyć. Aby uzyskać więcej informacji, zobacz [inline_recursion](../preprocessor/inline-recursion.md).

Inny pragma przydatne ograniczania głębokość wbudowanie jest `#pragma inline_depth`. Jest to zazwyczaj przydatne w sytuacjach, w którym ma być realizowany limit rozmiaru programu lub funkcji. Aby uzyskać więcej informacji, zobacz [inline_depth](../preprocessor/inline-depth.md).

## <a name="restrict-and-assume"></a>Element __restrict i \__assume

Istnieje kilka słów kluczowych w programie Visual Studio, które mogą pomóc wydajność: [element __restrict](../cpp/extension-restrict.md) i [__assume](../intrinsics/assume.md).

Po pierwsze należy zauważyć, że `__restrict` i `__declspec(restrict)` dwie różne rzeczy. Gdy nieco są powiązane, ich semantyki różnią się. `__restrict` jak jest kwalifikator typu `const` lub `volatile`, ale wyłącznie dla typów wskaźnika.

Wskaźnik, który jest modyfikowana za pomocą `__restrict` nazywa się *element __restrict wskaźnik*. Wskaźnik __restrict znajduje się wskaźnik, który jest możliwy tylko za pośrednictwem \__restrict wskaźnika. Innymi słowy, inny wskaźnik nie można uzyskać dostęp do danych wskazywanego przez \__restrict wskaźnika.

`__restrict` może być zaawansowanym narzędziem do firmy Microsoft C++ optimizer, ale jej używać z szczególną uwagę na. Jeśli używany nieprawidłowo, optymalizator może wykonywać optymalizację, które mogłyby spowodować przerwanie działania aplikacji.

`__restrict` Zastępuje słowo kluczowe **porównuje** przełączyć się z poprzednimi wersjami.

Za pomocą `__assume`, deweloper może każą kompilatorowi zakładają wartości niektórych zmiennej.

Na przykład `__assume(a < 5);` informuje Optymalizator, który w tym wierszu kodu zmiennej `a` jest mniejsza niż 5. To kolejna zmiana promise do kompilatora. Jeśli `a` jest faktycznie 6 na tym etapie w programie, a następnie zachowanie programu po optymalizacji kompilatora może nie być, czego można oczekiwać. `__assume` jest najbardziej użyteczne przed instrukcji switch i/lub wyrażenia warunkowe.

Istnieją pewne ograniczenia dotyczące `__assume`. Po pierwsze, takich jak `__restrict`, jest tylko sugestia, dzięki czemu kompilator jest bezpłatne go zignorować. Ponadto `__assume` obecnie działa tylko w przypadku zmiennych nierówności przed stałe. Go nie propaguje symboliczne nierówności, na przykład assume(a < b).

## <a name="intrinsic-support"></a>Wsparcie wewnętrznej

Funkcje wewnętrzne są funkcja wywołuje, której kompilator ma wewnętrzne wiedzę na temat wywołania, a zamiast wywołanie funkcji w bibliotece, emituje kod dla tej funkcji. Plik nagłówkowy \<intrin.h > zawiera wszystkie dostępne funkcje wewnętrzne dla każdej z platform obsługiwanego sprzętu.

Funkcje wewnętrzne pozwalają programistę na dogłębnego kod bez konieczności używania zestawu. Istnieje wiele korzyści związanych z przy użyciu funkcji wewnętrznych:

- Twój kod będzie bardziej przenośny. Niektóre funkcje wewnętrzne są dostępne na wielu architekturach procesora CPU.

- Kod jest łatwiejsza do odczytania, ponieważ kod nadal jest napisany w języku C/C++.

- Kod uzyskuje korzyści optymalizacje kompilatora. Ponieważ kompilator pobiera lepsze, poprawia generowanie kodu dla funkcji wewnętrznych.

Aby uzyskać więcej informacji, zobacz [funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md).

## <a name="exceptions"></a>Wyjątki

Brak wydajności trafień związanych z używaniem wyjątków. Pewne ograniczenia zostały wprowadzone, korzystając z bloków try Powstrzymaj kompilator wykonywać pewne optymalizacje. Na x86 bloki ze względu na informacje o stanie dodatkowe, które musi zostać wygenerowany podczas wykonywania kodu try zmniejszenie wydajności z różnych platform. Na platformach 64-bitowych spróbuj bloki nie obniżyć wydajność, tyle, ale gdy wyjątek jest generowany, proces znajdowania programu obsługi i odwinięcie stosu może być kosztowne.

W związku z tym zaleca się unikać wprowadzania bloków try/catch do kodu, który nie naprawdę potrzebne. Jeśli musisz użyć wyjątki, użyj synchronicznej wyjątków, jeśli jest to możliwe. Aby uzyskać więcej informacji, zobacz [obsługi wyjątków strukturalnych, (C/C++)](../cpp/structured-exception-handling-c-cpp.md).

Na koniec zgłaszają wyjątki, tylko wyjątkowych przypadków. Używanie wyjątków do przepływu sterowania ogólne prawdopodobnie spowoduje, że to spowodować obniżenie wydajności.

## <a name="see-also"></a>Zobacz także

- [Optymalizacja kodu](optimizing-your-code.md)
