---
title: Najlepsze rozwiązania dotyczące optymalizacji
ms.date: 05/06/2019
helpviewer_keywords:
- C++, optimization
- optimization, best practices
ms.assetid: f3433148-7255-4ca6-8a4f-7c31aac88508
ms.openlocfilehash: 541114b4cbf7d3d063e48b50ab265b4c95c6237c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328452"
---
# <a name="optimization-best-practices"></a>Najlepsze rozwiązania dotyczące optymalizacji

W tym dokumencie opisano niektóre najlepsze rozwiązania dotyczące optymalizacji programów języka C++ w programie Visual Studio.

## <a name="compiler-and-linker-options"></a>Opcje kompilatora i konsolidatora

### <a name="profile-guided-optimization"></a>Optymalizacja z przewodnikiem po profilach

Program Visual Studio obsługuje *optymalizację kierowaną profilem* (PGO). Ta optymalizacja wykorzystuje dane profilu z wykonywania szkolenia oprzyrządowane wersji aplikacji do kierowania później optymalizacji aplikacji. Korzystanie z PGO może być czasochłonne, więc może nie być czymś, czego używa każdy deweloper, ale zalecamy użycie PGO do ostatecznej kompilacji wersji produktu. Aby uzyskać więcej informacji, zobacz [Optymalizacje z przewodnikiem profilu](profile-guided-optimizations.md).

Ponadto *optymalizacja całego programu* (znana również jako generowanie kodu czasu łącza) i optymalizacje **/O1** i **/O2** zostały ulepszone. Ogólnie rzecz biorąc aplikacja skompilowana przy jednej z tych opcji będzie szybsza niż ta sama aplikacja skompilowana z wcześniejszym kompilatorem.

Aby uzyskać więcej informacji, zobacz [/GL (Optymalizacja całego programu)](reference/gl-whole-program-optimization.md) i [/O1, /O2 (Minimalizuj rozmiar, Maksymalizuj szybkość)](reference/o1-o2-minimize-size-maximize-speed.md).

### <a name="which-level-of-optimization-to-use"></a>Jaki poziom optymalizacji użyć

Jeśli w ogóle jest to możliwe, kompilacje wersji końcowej powinny być kompilowane z optymalizacjami z przewodnikiem profilu. Jeśli nie jest możliwe do zbudowania z PGO, czy z powodu niewystarczającej infrastruktury do uruchamiania oprzyrządowanych kompilacji lub nie mając dostępu do scenariuszy, a następnie proponujemy tworzenie z optymalizacji całego programu.

Przełącznik **/Gy** jest również bardzo przydatny. Generuje oddzielny COMDAT dla każdej funkcji, co daje konsolidator większą elastyczność, jeśli chodzi o usuwanie nieodwołonowych COMDATs i comdat składania. Jedynym minusem przy użyciu **/Gy** jest to, że może powodować problemy podczas debugowania. W związku z tym, ogólnie zaleca się go używać. Aby uzyskać więcej informacji, zobacz [/Gy (Włącz łączenie na poziomie funkcji)](reference/gy-enable-function-level-linking.md).

W przypadku łączenia w środowiskach 64-bitowych zaleca się użycie opcji konsolidatora **/OPT:REF,ICF,** a w środowiskach 32-bitowych zaleca się użycie opcji /OPT:REF. **/OPT:REF** Aby uzyskać więcej informacji, zobacz [/OPT (Optymalizacje)](reference/opt-optimizations.md).

Zdecydowanie zaleca się również generowanie symboli debugowania, nawet w zoptymalizowanych kompilacjach wersji. Nie ma to wpływu na wygenerowany kod i znacznie ułatwia debugowanie aplikacji, jeśli zajdzie taka potrzeba.

### <a name="floating-point-switches"></a>Przełączniki zmiennoprzecinowe

Usunięto opcję kompilatora **/Op** i dodano następujące cztery opcje kompilatora dotyczące optymalizacji zmiennoprzecinkowych:

|||
|-|-|
|**/fp:precyzyjny**|Jest to domyślne zalecenie i powinny być używane w większości przypadków.|
|**/fp:szybki**|Zalecane, jeśli wydajność jest sprawą najwyższej wagi, na przykład w grach. Spowoduje to najszybszą wydajność.|
|**/fp:ścisły**|Zalecane, jeśli zalecane jest precyzyjne wyjątki zmiennoprzecinające i zachowanie IEEE. Spowoduje to najwolniejszą wydajność.|
|**/fp:z wyjątkiem[-]**|Może być używany w połączeniu z **/fp:strict** lub **/fp:precise**, ale nie **/fp:fast**.|

Aby uzyskać więcej informacji, zobacz [/fp (Określ zachowanie zmiennoprzecinkowe)](reference/fp-specify-floating-point-behavior.md).

## <a name="optimization-declspecs"></a>Declspecs optymalizacji

W tej sekcji przyjrzymy się dwóm declspecs, które `__declspec(restrict)` `__declspec(noalias)`mogą być używane w programach, aby pomóc wydajność: i .

Declspec `restrict` można zastosować tylko do deklaracji funkcji, które zwracają wskaźnik, takich jak`__declspec(restrict) void *malloc(size_t size);`

Declspec `restrict` jest używany na funkcje, które zwracają niealiasowanych wskaźników. To słowo kluczowe jest używane dla implementacji biblioteki `malloc` C-Runtime, ponieważ nigdy nie zwróci wartości wskaźnika, która jest już używana w bieżącym programie (chyba że robisz coś niezgodnego z prawem, na przykład przy użyciu pamięci po jej zwolnieniu).

Declspec `restrict` daje kompilatorowi więcej informacji do wykonywania optymalizacji kompilatora. Jedną z najtrudniejszych rzeczy dla kompilatora, aby określić, jakie wskaźniki alias innych wskaźników i przy użyciu tych informacji znacznie pomaga kompilatora.

Warto podkreślić, że jest to obietnica dla kompilatora, a nie coś, co kompilator zweryfikuje. Jeśli program używa `restrict` tej declspec niewłaściwie, program może mieć nieprawidłowe zachowanie.

Aby uzyskać więcej informacji, zobacz [ograniczanie](../cpp/restrict.md).

Declspec `noalias` jest również stosowany tylko do funkcji i wskazuje, że funkcja jest funkcją półczystą. Funkcja półczystości jest taka, która odwołuje się lub modyfikuje tylko mieszkańców, argumenty i pośrednie argumenty pierwszego poziomu. Ta declspec jest obietnicą dla kompilatora, a jeśli funkcja odwołuje się globals lub drugiego poziomu pośrednie argumenty wskaźnika następnie kompilator może wygenerować kod, który przerywa aplikacji.

Aby uzyskać więcej informacji, zobacz [noalias](../cpp/noalias.md).

## <a name="optimization-pragmas"></a>Pragmas optymalizacji

Istnieje również kilka przydatnych pragmy ułatwianie optymalizacji kodu. Pierwszym z nich omówimy `#pragma optimize`to:

```cpp
#pragma optimize("{opt-list}", on | off)
```

Pragma ta pozwala ustawić dany poziom optymalizacji na podstawie funkcji po funkcji. Jest to idealne rozwiązanie dla tych rzadkich przypadkach, w których aplikacja ulega awarii, gdy dana funkcja jest kompilowana z optymalizacją. Można użyć tego, aby wyłączyć optymalizacje dla jednej funkcji:

```cpp
#pragma optimize("", off)
int myFunc() {...}
#pragma optimize("", on)
```

Aby uzyskać więcej informacji, zobacz [optymalizacja](../preprocessor/optimize.md).

Inlining jest jednym z najważniejszych optymalizacji, które wykonuje kompilator i tutaj mówimy o kilku pragmy, które pomagają zmodyfikować to zachowanie.

`#pragma inline_recursion`jest przydatne do określenia, czy aplikacja ma być w stanie wbudowane wywołania cyklicznego. Domyślnie jest wyłączony. W przypadku płytkiej rekursji małych funkcji można to włączyć. Aby uzyskać więcej informacji, zobacz [inline_recursion](../preprocessor/inline-recursion.md).

Innym przydatnym pragmą do ograniczania `#pragma inline_depth`głębokości inline jest . Jest to zazwyczaj przydatne w sytuacjach, gdy próbujesz ograniczyć rozmiar programu lub funkcji. Aby uzyskać więcej informacji, zobacz [inline_depth](../preprocessor/inline-depth.md).

## <a name="__restrict-and-__assume"></a>__restrict i \__assume

W programie Visual Studio znajduje się kilka słów kluczowych, które mogą pomóc w wydajności: [__restrict](../cpp/extension-restrict.md) i [__assume](../intrinsics/assume.md).

Po pierwsze, należy `__restrict` zauważyć, że i `__declspec(restrict)` są dwie różne rzeczy. Chociaż są one nieco związane, ich semantyka jest inna. `__restrict`jest kwalifikatorem typu, takim jak `const` lub `volatile`, ale wyłącznie dla typów wskaźników.

Wskaźnik, który jest `__restrict` modyfikowany za pomocą jest określany jako *wskaźnik __restrict*. Wskaźnik __restrict to wskaźnik, do który można uzyskać \_dostęp tylko za pośrednictwem _restrict wskaźnika. Innymi słowy inny wskaźnik nie może służyć do dostępu \_do danych wskazywali przez wskaźnik _restrict.

`__restrict`może być potężnym narzędziem dla optymalizatora Microsoft C++, ale używaj go z wielką starannością. Jeśli jest używany nieprawidłowo, optymalizator może wykonać optymalizację, która spowoduje przerwanie aplikacji.

Słowo `__restrict` kluczowe zastępuje przełącznik **/Oa** z poprzednich wersji.

Z `__assume`, deweloper może powiedzieć kompilator do założeń dotyczących wartości niektórych zmiennych.

Na `__assume(a < 5);` przykład informuje optymalizatora, że `a` w tym wierszu kodu zmienna jest mniejsza niż 5. Ponownie jest to obietnica dla kompilatora. Jeśli `a` jest rzeczywiście 6 w tym momencie w programie to zachowanie programu po zoptymalizowany kompilator może nie być to, czego można się spodziewać. `__assume`jest najbardziej przydatne przed przełączeniem instrukcji i/lub wyrażeń warunkowych.

Istnieją pewne ograniczenia `__assume`. Po pierwsze, jak `__restrict`, jest to tylko sugestia, więc kompilator może go zignorować. Ponadto `__assume` obecnie działa tylko ze zmiennymi nierównościami względem stałych. Nie propaguje symboliczne nierówności, na przykład zakłada(a < b).

## <a name="intrinsic-support"></a>Wewnętrzna pomoc techniczna

Wewnętrzne są wywołania funkcji, gdzie kompilator ma wewnętrzną wiedzę na temat wywołania i zamiast wywoływania funkcji w bibliotece, emituje kod dla tej funkcji. Plik \<nagłówka intrin.h> zawiera wszystkie dostępne elementy wewnętrzne dla każdej z obsługiwanych platform sprzętowych.

Wewnętrzne umożliwia programistom możliwość zagłębienia się w kod bez konieczności używania zestawu. Istnieje kilka korzyści z używania wewnętrznego:

- Kod jest bardziej przenośny. Kilka wewnętrznych są dostępne na wielu architekturach procesora CPU.

- Kod jest łatwiejszy do odczytania, ponieważ kod jest nadal napisany w języku C/C++.

- Kod pobiera korzyści optymalizacji kompilatora. Jak kompilator staje się lepiej, generowanie kodu dla intrinsics poprawia.

Aby uzyskać więcej informacji, zobacz [Intrinsics kompilatora](../intrinsics/compiler-intrinsics.md).

## <a name="exceptions"></a>Wyjątki

Występuje trafienie wydajności skojarzone z przy użyciu wyjątków. Niektóre ograniczenia są wprowadzane podczas korzystania z try bloków, które uniemożliwiają kompilatorowi wykonywanie pewnych optymalizacji. Na platformach x86 występuje dodatkowe obniżenie wydajności z try bloków ze względu na dodatkowe informacje o stanie, które muszą być generowane podczas wykonywania kodu. Na platformach 64-bitowych try bloki nie obniżyć wydajność tak bardzo, ale po wyjątek, proces znajdowania obsługi i odwijania stosu może być kosztowne.

W związku z tym zaleca się, aby uniknąć wprowadzania try/catch bloków do kodu, który tak naprawdę nie potrzebuje. Jeśli należy użyć wyjątków, należy użyć wyjątków synchronicznych, jeśli to możliwe. Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md).

Nareszcie zgłaszaj wyjątki tylko w wyjątkowych przypadkach. Używanie wyjątków dla ogólnego przepływu sterowania prawdopodobnie spowoduje, że wydajność będzie cierpieć.

## <a name="see-also"></a>Zobacz też

- [Optymalizacja kodu](optimizing-your-code.md)
