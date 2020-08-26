---
title: Najlepsze rozwiązania dotyczące optymalizacji
ms.date: 05/06/2019
helpviewer_keywords:
- C++, optimization
- optimization, best practices
ms.assetid: f3433148-7255-4ca6-8a4f-7c31aac88508
ms.openlocfilehash: 425fa0bb6b7aab502ce493ced8b587fad8ce59a8
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833351"
---
# <a name="optimization-best-practices"></a>Najlepsze rozwiązania dotyczące optymalizacji

W tym dokumencie opisano niektóre najlepsze rozwiązania dotyczące optymalizacji programów C++ w programie Visual Studio.

## <a name="compiler-and-linker-options"></a>Opcje kompilatora i konsolidatora

### <a name="profile-guided-optimization"></a>Optymalizacja oparta na profilach

Program Visual Studio obsługuje *optymalizację* profilowaną (PGO). Ta optymalizacja używa danych profilowych z wykonywania szkoleniowego w ramach Instrumentacji wersji aplikacji, aby zwiększyć optymalizację aplikacji. Korzystanie z programu PGO może być czasochłonne, dlatego może nie być coś, co jest używane przez każdego dewelopera, ale zalecamy użycie PGO do ostatecznej kompilacji produktu. Aby uzyskać więcej informacji, zapoznaj się z tematem [optymalizacje](profile-guided-optimizations.md)profilowane.

Dodatkowo *Optymalizacja całego programu* (znana również jako generowanie kodu w czasie konsolidacji) oraz **`/O1`** **`/O2`** udoskonalona Optymalizacja i optymalizacje. Ogólnie rzecz biorąc, aplikacja skompilowana przy użyciu jednej z tych opcji będzie szybsza niż ta sama aplikacja skompilowana przy użyciu wcześniejszego kompilatora.

Aby uzyskać więcej informacji, zobacz [ `/GL` (Optymalizacja całego programu)](reference/gl-whole-program-optimization.md) i [ `/O1` , `/O2` (Minimalizuj rozmiar, maksymalizuj szybkość)](reference/o1-o2-minimize-size-maximize-speed.md).

### <a name="which-level-of-optimization-to-use"></a>Jakiego poziomu optymalizacji użyć

Jeśli to możliwe, ostateczne kompilacje wydania powinny być kompilowane przy użyciu optymalizacji profilowanej. Jeśli nie jest możliwe Kompilowanie przy użyciu usługi PGO, niezależnie od tego, czy z powodu niewystarczającej infrastruktury do uruchamiania kompilacji z instrumentacją lub nie ma dostępu do scenariuszy, zalecamy Kompilowanie za pomocą całościowej optymalizacji programu.

**`/Gy`** Przełącznik jest również bardzo przydatny. Generuje osobne COMDAT dla każdej funkcji, dzięki czemu konsolidator ma większą elastyczność, gdy nastąpi usunięcie COMDAT i złożenia COMDAT. Jedyną minusemą do użycia **`/Gy`** jest to, że może to spowodować problemy podczas debugowania. W związku z tym zwykle zaleca się jej użycie. Aby uzyskać więcej informacji, zobacz [ `/Gy` (Włącz łączenie na poziomie funkcji)](reference/gy-enable-function-level-linking.md).

W przypadku łączenia w środowiskach 64-bitowych zaleca się użycie **`/OPT:REF,ICF`** opcji konsolidatora i w środowiskach 32-bitowych **`/OPT:REF`** . Aby uzyskać więcej informacji, zobacz [/opt (optymalizacje)](reference/opt-optimizations.md).

Zdecydowanie zaleca się również generowanie symboli debugowania, nawet w przypadku zoptymalizowanych kompilacji wydań. Nie ma to wpływu na wygenerowany kod i ułatwia debugowanie aplikacji, jeśli jest to konieczne.

### <a name="floating-point-switches"></a>Przełączniki zmiennoprzecinkowe

**`/Op`** Opcja kompilatora została usunięta i dodano następujące cztery opcje kompilatora dotyczące optymalizacji zmiennoprzecinkowej:

|Opcja|Opis|
|-|-|
|**`/fp:precise`**|Jest to domyślne zalecenie i powinno być używane w większości przypadków.|
|**`/fp:fast`**|Zalecane, jeśli wydajność ma najwyższą ważność, na przykład w grach. Spowoduje to najszybszą wydajność.|
|**`/fp:strict`**|Zalecane, jeśli wymagane są dokładne wyjątki zmiennoprzecinkowe i zachowanie IEEE. Spowoduje to wolniejszą wydajność.|
|**`/fp:except[-]`**|Może być używany w połączeniu z **`/fp:strict`** lub **`/fp:precise`** , ale nie **`/fp:fast`** .|

Aby uzyskać więcej informacji, zobacz [ `/fp` (Określanie zachowania zmiennoprzecinkowego)](reference/fp-specify-floating-point-behavior.md).

## <a name="optimization-declspecs"></a>Optymalizacja declspecs

W tej sekcji przeszukamy dwie declspecs, które mogą być używane w programach, aby pomóc w wydajności: `__declspec(restrict)` i `__declspec(noalias)` .

`restrict`Declspec można stosować tylko do deklaracji funkcji, które zwracają wskaźnik, taki jak`__declspec(restrict) void *malloc(size_t size);`

`restrict`Declspec jest używany w funkcjach zwracających wskaźniki niealiasowe. To słowo kluczowe jest używane w implementacji biblioteki środowiska uruchomieniowego języka C, `malloc` ponieważ nigdy nie zwróci wartości wskaźnika, która jest już używana w bieżącym programie (chyba że wykonujesz coś niedozwolonego, na przykład użycie pamięci po jej zwolnieniu).

`restrict`Declspec zapewnia kompilatorowi więcej informacji na potrzeby wykonywania optymalizacji kompilatora. Jednym z najtrudniejszych elementów kompilatora, aby określić, czy wskaźniki są aliasem innych wskaźników, a korzystanie z tych informacji jest znacznie pomocne w kompilatorze.

Warto wskazać, że jest to obietnica do kompilatora, a nie do sprawdzenia, czy kompilator sprawdzi. Jeśli program używa tego `restrict` declspec w niewłaściwy sposób, program może mieć nieprawidłowe zachowanie.

Aby uzyskać więcej informacji, zobacz [`restrict`](../cpp/restrict.md).

`noalias`Declspec jest również stosowany tylko do funkcji i wskazuje, że funkcja jest funkcją podzielonej. Funkcja częściowo czysta to taka, która odwołuje się do lub modyfikuje tylko wartości lokalne, argumenty i wartości pośrednie pierwszego poziomu argumentów. Ten declspec jest obietnicą kompilatora, a jeśli funkcja odwołuje się do Globals lub drugiego przekierowania argumentów wskaźnika, kompilator może wygenerować kod, który rozdzieli aplikację.

Aby uzyskać więcej informacji, zobacz [`noalias`](../cpp/noalias.md).

## <a name="optimization-pragmas"></a>Dyrektywy pragma optymalizacji

Istnieje również kilka przydatnych pragm ułatwiających optymalizację kodu. Pierwsza z nich zostanie omówiona `#pragma optimize` :

```cpp
#pragma optimize("{opt-list}", on | off)
```

Ta pragma umożliwia ustawienie określonego poziomu optymalizacji w odniesieniu do funkcji. Jest to idealne rozwiązanie w rzadkich przypadkach, gdy aplikacja ulega awarii, gdy dana funkcja jest skompilowana z optymalizacją. Możesz użyć tej opcji, aby wyłączyć optymalizacje dla jednej funkcji:

```cpp
#pragma optimize("", off)
int myFunc() {...}
#pragma optimize("", on)
```

Aby uzyskać więcej informacji, zobacz [`optimize`](../preprocessor/optimize.md).

Funkcja tworzenia konspektu jest jednym z najważniejszych optymalizacji, które wykonuje kompilator, i tutaj porozmawiamy o kilku pragmach, które pomagają zmodyfikować to zachowanie.

`#pragma inline_recursion` jest przydatne do określania, czy aplikacja ma mieć możliwość wbudowania wywołania cyklicznego. Domyślnie jest on wyłączony. W przypadku płytkiej rekursji małych funkcji można ją włączyć. Aby uzyskać więcej informacji, zobacz [`inline_recursion`](../preprocessor/inline-recursion.md).

Kolejną przydatną pragmą ograniczającą głębokość wykreślania jest `#pragma inline_depth` . Jest to zazwyczaj przydatne w sytuacjach, w których próbujesz ograniczyć rozmiar programu lub funkcji. Aby uzyskać więcej informacji, zobacz [`inline_depth`](../preprocessor/inline-depth.md).

## <a name="__restrict-and-__assume"></a>`__restrict` i `__assume`

W programie Visual Studio istnieje kilka słów kluczowych, które mogą pomóc w wydajności: [__restrict](../cpp/extension-restrict.md) i [__assume](../intrinsics/assume.md).

Najpierw należy zauważyć, że **`__restrict`** i `__declspec(restrict)` są dwa różne rzeczy. Chociaż są one nieco powiązane, ich semantyka różni się. **`__restrict`** jest kwalifikatorem typu, takim jak **`const`** lub **`volatile`** , ale wyłącznie dla typów wskaźnika.

Wskaźnik, który został zmodyfikowany przy użyciu, **`__restrict`** jest określany jako *wskaźnik __restrict*. Wskaźnik __restrict jest wskaźnikiem, do którego można uzyskać dostęp tylko za pomocą \_ wskaźnika _restrict. Innymi słowy, inny wskaźnik nie może być używany w celu uzyskania dostępu do danych wskazywanych przez \_ wskaźnik _restrict.

**`__restrict`** może to być zaawansowane narzędzie dla Optymalizatora języka Microsoft C++, ale korzystaj z niego bardzo ostrożnie. W przypadku nieprawidłowego użycia Optymalizator może przeprowadzić optymalizację, która spowodowałaby uszkodzenie aplikacji.

**`__restrict`** Słowo kluczowe zastępuje przełącznik **/OA** z poprzednich wersji.

W programie **`__assume`** deweloper może powiedzieć kompilatorowi, aby założeń o wartości niektórych zmiennych.

Na przykład `__assume(a < 5);` instruuje optymalizator, że w tym wierszu kodu zmienna `a` jest mniejsza niż 5. Ponownie jest to obietnica do kompilatora. Jeśli `a` program jest w rzeczywistości 6 w tym momencie w programie, zachowanie programu po zoptymalizowaniu kompilatora może nie być oczekiwane. **`__assume`** jest najbardziej przydatne przed przełączeniem instrukcji i/lub wyrażeń warunkowych.

Istnieją pewne ograniczenia dotyczące programu **`__assume`** . Najpierw, podobnie jak **`__restrict`** , jest tylko sugestią, więc kompilator jest bezpłatny, aby go zignorować. Ponadto **`__assume`** obecnie działa tylko z zmienną nierówności względem stałych. Nie propaguje symbolicznych nierówności, na przykład załóżmy (a < b).

## <a name="intrinsic-support"></a>Obsługa wewnętrzna

Elementy wewnętrzne to wywołania funkcji, w których kompilator ma wewnętrzną wiedzę na temat wywołania, a nie do wywoływania funkcji w bibliotece, emituje kod dla tej funkcji. Plik nagłówkowy \<intrin.h> zawiera wszystkie dostępne elementy wewnętrzne dla każdej z obsługiwanych platform sprzętowych.

Funkcje wewnętrzne zapewniają programistom możliwość dokładnego przechodzenia do kodu bez konieczności używania zestawu. Istnieje kilka korzyści związanych z korzystaniem z funkcji wewnętrznych:

- Twój kod jest bardziej przenośny. Niektóre funkcje wewnętrzne są dostępne w wielu architekturach procesora CPU.

- Kod jest łatwiejszy do odczytania, ponieważ kod jest nadal pisany w C/C++.

- Twój kod uzyskuje korzyści wynikające z optymalizacji kompilatora. Gdy kompilator jest lepszym rozwiązaniem, generowanie kodu dla elementów wewnętrznych zwiększa się.

Aby uzyskać więcej informacji, zobacz elementy [Wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md).

## <a name="exceptions"></a>Wyjątki

Osiągnięto wydajność skojarzoną z wyjątkami. Niektóre ograniczenia są wprowadzane podczas korzystania z bloków try, które uniemożliwiają kompilatorowi wykonywanie pewnych optymalizacji. Na platformach x86 istnieje dodatkowe obniżenie wydajności z bloków try ze względu na dodatkowe informacje o stanie, które muszą zostać wygenerowane podczas wykonywania kodu. Na platformach 64-bitowych Wypróbuj bloki nie obniżają wydajności tak dużo, ale po zgłoszeniu wyjątku proces wyszukiwania programu obsługi i rozwinięcia stosu może być kosztowny.

Dlatego zaleca się unikanie wprowadzania bloków try/catch do kodu, który nie jest w rzeczywistości potrzebny. Jeśli musisz użyć wyjątków, Użyj wyjątków synchronicznych, jeśli to możliwe. Aby uzyskać więcej informacji, zobacz [strukturalna obsługa wyjątków (C/C++)](../cpp/structured-exception-handling-c-cpp.md).

Na koniec Zgłoś wyjątki tylko w przypadku wyjątkowych przypadków. Użycie wyjątków dla ogólnego przepływu sterowania prawdopodobnie spowoduje pogorszenie wydajności.

## <a name="see-also"></a>Zobacz też

- [Optymalizowanie kodu](optimizing-your-code.md)
