---
title: /fp (Określenie zachowania zmiennoprzecinkowego)
ms.date: 11/09/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.floatingPointModel
- VC.Project.VCCLWCECompilerTool.FloatingPointExceptions
- /fp
- VC.Project.VCCLWCECompilerTool.floatingPointModel
- VC.Project.VCCLCompilerTool.FloatingPointExceptions
helpviewer_keywords:
- -fp compiler option [C++]
- /fp compiler option [C++]
ms.assetid: 10469d6b-e68b-4268-8075-d073f4f5d57e
ms.openlocfilehash: f85f9b397ef3ab5bd070be1f4c81845405b14020
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234383"
---
# <a name="fp-specify-floating-point-behavior"></a>/fp (Określenie zachowania zmiennoprzecinkowego)

Określa sposób, w jaki kompilator traktuje wyrażenia zmiennoprzecinkowe, optymalizacje i wyjątki. Opcje **/FP** określają, czy wygenerowany kod umożliwia wprowadzanie zmian w środowisku zmiennoprzecinkowym do trybu zaokrąglania, masek wyjątków i zachowania nienormalnego oraz czy testy stanu zmiennoprzecinkowego zwracają bieżące, dokładne wyniki. Określa, czy kompilator generuje kod, który przechowuje operacje źródłowe i porządkowanie wyrażeń i jest zgodna ze standardem dla propagacji NaN, lub jeśli zamiast tego generuje bardziej wydajny kod, który może zmienić kolejność lub łączenie operacji i użyć uproszczenia transformacji algebraicznych, które nie są dozwolone przez Standard.

## <a name="syntax"></a>Składnia

> **/FP:**[**precyzyjne**  |  **ścisłe**,  |  **fast**  |  **z wyjątkiem**[ **-** ]]

### <a name="arguments"></a>Argumenty

#### <a name="precise"></a>określone

Domyślnie kompilator używa `/fp:precise` zachowania.

W `/fp:precise` kompilatorze zachowuje właściwości porządkowania i zaokrąglania wyrażenia źródłowego kodu zmiennoprzecinkowego, gdy generuje i optymalizuje kod obiektu dla maszyny docelowej. Kompilator zaokrągla do dokładności kodu źródłowego w czterech określonych punktach podczas obliczania wyrażenia: na typecasts, gdy argument zmiennoprzecinkowy jest przesyłany do wywołania funkcji i gdy wartość zmiennoprzecinkowa jest zwracana z wywołania funkcji. Obliczenia pośrednie mogą być wykonywane z dokładnością maszyny. Typecasts może służyć do jawnego zaokrąglania pośrednich obliczeń.

Kompilator nie wykonuje transformacji algebraicznych w wyrażeniach zmiennoprzecinkowych, takich jak ponowne skojarzenie lub dystrybucja, chyba że transformacja ma na celu wygenerowanie bitowej identycznego wyniku.
Wyrażenia, które obejmują specjalne wartości (NaN, + nieskończoność, nieskończoność,-0,0) są przetwarzane zgodnie ze specyfikacjami IEEE-754. Na przykład, `x != x` daje w **`true`** przypadku, gdy x jest NaN. Nieruchome *kontrakty*, czyli instrukcje dotyczące maszyn, które łączą operacje zmiennoprzecinkowe, mogą być generowane w ramach `/fp:precise` .

Kompilator generuje kod przeznaczony do uruchamiania w [domyślnym środowisku zmiennoprzecinkowym](#the-default-floating-point-environment) i zakłada, że środowisko zmiennoprzecinkowe nie jest dostępne ani modyfikowane w czasie wykonywania. Oznacza to, że założono, że kod nie rozmaskuje wyjątków zmiennoprzecinkowych, odczytuje lub zapisuje rejestry stanu zmiennoprzecinkowego lub zmienia tryby zaokrąglania.

Jeśli kod zmiennoprzecinkowy nie zależy od kolejności operacji i wyrażeń w instrukcjach zmiennoprzecinkowych (na przykład jeśli nie ma znaczenia, czy `a * b + a * c` jest obliczany jako `(b + c) * a` lub `2 * a` jako `a + a` ), rozważ użycie opcji [/FP: Fast](#fast) , która może generować szybszy i bardziej wydajny kod. Jeśli Twój kod zależy od kolejności operacji i wyrażeń i uzyskuje dostęp do środowiska zmiennoprzecinkowego (na przykład w celu zmiany trybów zaokrąglania lub w celu przetworzenia wyjątków zmiennoprzecinkowych), użyj [/FP: Strict](#strict).

#### <a name="strict"></a>ściśle

`/fp:strict`ma zachowanie podobne do `/fp:precise` , to oznacza, że kompilator zachowuje właściwości określania kolejności źródłowej i zaokrąglania kodu zmiennoprzecinkowego, gdy generuje i optymalizuje kod obiektu dla maszyny docelowej, i obserwuje Standard podczas obsługi wartości specjalnych. Ponadto program może bezpiecznie uzyskać dostęp lub zmodyfikować środowisko zmiennoprzecinkowe w czasie wykonywania.

W obszarze `/fp:strict` , kompilator generuje kod, który umożliwia programowi bezpieczne anulowanie maskowania wyjątków zmiennoprzecinkowych, Odczyt lub zapis rejestrów stanu zmiennoprzecinkowego lub zmienianie trybów zaokrąglania. Jest ona zaokrąglana do dokładności kodu źródłowego w czterech określonych punktach podczas obliczania wyrażenia: w przypisaniach w typecasts, gdy argument zmiennoprzecinkowy jest przesyłany do wywołania funkcji i gdy wartość zmiennoprzecinkowa jest zwracana z wywołania funkcji. Obliczenia pośrednie mogą być wykonywane z dokładnością maszyny. Typecasts może służyć do jawnego zaokrąglania pośrednich obliczeń. Kompilator nie wykonuje transformacji algebraicznych w wyrażeniach zmiennoprzecinkowych, takich jak ponowne skojarzenie lub dystrybucja, chyba że transformacja ma na celu wygenerowanie bitowej identycznego wyniku. Wyrażenia, które obejmują specjalne wartości (NaN, + nieskończoność, nieskończoność,-0,0) są przetwarzane zgodnie ze specyfikacjami IEEE-754. Na przykład, `x != x` daje w **`true`** przypadku, gdy x jest NaN. Kontrakty zmiennoprzecinkowe nie są generowane w ramach `/fp:strict` .

`/fp:strict`jest bardziej kosztowny niż `/fp:precise` ponieważ kompilator musi wstawić dodatkowe instrukcje dotyczące wyjątków pułapek i zezwalać programom na dostęp lub modyfikowanie środowiska zmiennoprzecinkowego w czasie wykonywania. Jeśli kod nie korzysta z tej możliwości, ale wymaga uporządkowania i zaokrąglania kodu źródłowego lub opiera się na wartościach specjalnych, użyj `/fp:precise` . W przeciwnym razie Rozważ użycie `/fp:fast` , co może spowodować szybsze i mniejsze kod.

#### <a name="fast"></a>szybki

`/fp:fast`Opcja umożliwia kompilatorowi zmianę kolejności, łączenia lub uproszczenie operacji zmiennoprzecinkowych w celu zoptymalizowania kodu zmiennoprzecinkowego pod kątem szybkości i miejsca. Kompilator może pominąć zaokrąglenie w instrukcjach przypisania, typecasts lub wywołaniach funkcji. Może zmienić kolejność operacji lub wykonywać transformacje algebraicznych, na przykład przy użyciu funkcji kojarzenia i rozdzielania, nawet jeśli takie przekształcenia spowodują zaobserwowanie innych zachowań zaokrąglania. Ze względu na rozszerzoną optymalizację wynik niektórych obliczeń zmiennoprzecinkowych może się różnić od tych utworzonych przez inne `/fp` Opcje. Wartości specjalne (NaN, + nieskończoność,-Infinity,-0,0) nie mogą być propagowane lub działać ściśle zgodnie ze standardem IEEE-754. Kontrakty zmiennoprzecinkowe mogą być generowane w ramach `/fp:fast` . Kompilator nadal jest powiązany z podstawową architekturą `/fp:fast` , a dodatkowe optymalizacje mogą być dostępne za pomocą opcji [/Arch](arch-minimum-cpu-architecture.md) .

W obszarze `/fp:fast` kompilator generuje kod przeznaczony do uruchomienia w domyślnym środowisku zmiennoprzecinkowym i zakłada, że środowisko zmiennoprzecinkowe nie jest dostępne ani modyfikowane w czasie wykonywania. Oznacza to, że założono, że kod nie rozmaskuje wyjątków zmiennoprzecinkowych, odczytuje lub zapisuje rejestry stanu zmiennoprzecinkowego lub zmienia tryby zaokrąglania.

`/fp:fast`Program jest przeznaczony dla programów, które nie wymagają dokładnego porządkowania kodu źródłowego i zaokrąglania wyrażeń zmiennoprzecinkowych, i nie opierają się na standardowych regułach obsługi wartości specjalnych, takich jak NaN. Jeśli kod zmiennoprzecinkowy wymaga zachowywania kolejności i zaokrąglania kodu źródłowego, lub opiera się na standardowym zachowaniu specjalnych wartości, użyj [/FP: precyzyjne](#precise). Jeśli kod uzyskuje dostęp do środowiska zmiennoprzecinkowego lub modyfikuje je, aby zmienić tryby zaokrąglania, anulować wyjątki zmiennoprzecinkowe lub sprawdzić stan zmiennoprzecinkowy, użyj [/FP: Strict](#strict).

#### <a name="except"></a>ale

`/fp:except`Opcja generuje kod w celu zagwarantowania, że wszystkie niemaskowane wyjątki zmiennoprzecinkowe są zgłaszane w miejscu, w którym występują, i że nie są zgłaszane żadne dodatkowe wyjątki zmiennoprzecinkowe. Domyślnie `/fp:strict` opcja włącza `/fp:except` i nie `/fp:precise` . `/fp:except`Opcja nie jest zgodna z programem `/fp:fast` . Opcja może być jawnie wyłączona przez firmę Microsoft `/fp:except-` .

Należy pamiętać, że program nie `/fp:except` włącza żadnych wyjątków zmiennoprzecinkowych przez siebie, ale jest to wymagane w celu włączenia wyjątków zmiennoprzecinkowych. Aby uzyskać informacje na temat włączania wyjątków zmiennoprzecinkowych, zobacz [_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md) .

## <a name="remarks"></a>Uwagi

`/fp`W tym samym wierszu polecenia kompilatora można określić wiele opcji. Tylko jedna z `/fp:strict` `/fp:fast` opcji, i `/fp:precise` może działać jednocześnie. Jeśli w wierszu polecenia określono więcej niż jedną z tych opcji, ta opcja ma pierwszeństwo, a kompilator generuje ostrzeżenie. `/fp:strict`Opcje i `/fp:except` nie są zgodne z programem `/clr` .

Opcja [/za](za-ze-disable-language-extensions.md) (zgodność ze standardem ANSI) nie jest zgodna z programem `/fp` .

### <a name="using-compiler-directives-to-control-floating-point-behavior"></a>Używanie dyrektyw kompilatora do kontrolowania zachowań zmiennoprzecinkowych

Kompilator oferuje trzy dyrektywy pragma, aby zastąpić zachowanie zmiennoprzecinkowe określone w wierszu polecenia: [float_control](../../preprocessor/float-control.md), [fenv_access](../../preprocessor/fenv-access.md)i [fp_contract](../../preprocessor/fp-contract.md). Za pomocą tych dyrektyw można kontrolować zachowanie zmiennoprzecinkowe na poziomie funkcji, a nie w ramach funkcji. Należy zauważyć, że dyrektywy te nie odpowiadają bezpośrednio na `/fp` Opcje. W tej tabeli pokazano, jak `/fp` Opcje i dyrektywy pragma są mapowane na siebie nawzajem. Aby uzyskać więcej informacji, zobacz dokumentację poszczególnych opcji i dyrektywy pragma.

||float_control (precyzyjne)|float_control (z wyjątkiem)|fenv_access|fp_contract|
|-|-|-|-|-|
|`/fp:fast`|wyłączone|wyłączone|wyłączone|on|
|`/fp:precise`|on|wyłączone|wyłączone|on|
|`/fp:strict`|on|on|on|wyłączone|

### <a name="the-default-floating-point-environment"></a>Domyślne środowisko zmiennoprzecinkowe

Po zainicjowaniu procesu jest ustawiane *domyślne środowisko zmiennoprzecinkowe* . To środowisko maskuje wszystkie wyjątki zmiennoprzecinkowe, ustawia tryb zaokrąglania do najbliższego ( `FE_TONEAREST` ), zachowując normalne (nienormalne) wartości, używa domyślnej precyzji mantysę (mantysy) dla **`float`** , **`double`** , i **`long double`** , jeśli jest to obsługiwane, ustawia w formancie nieskończoność domyślny tryb afinicznym.

### <a name="floating-point-environment-access-and-modification"></a>Dostęp do środowiska zmiennoprzecinkowego i modyfikacje

Środowisko uruchomieniowe Microsoft Visual C++ udostępnia kilka funkcji, które umożliwiają dostęp i modyfikowanie środowiska zmiennoprzecinkowego. Obejmują one [_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md), [_clearfp](../../c-runtime-library/reference/clear87-clearfp.md)i [_statusfp](../../c-runtime-library/reference/status87-statusfp-statusfp2.md) oraz ich wariantów. Aby zapewnić poprawne zachowanie programu, gdy kod uzyskuje dostęp do środowiska zmiennoprzecinkowego lub modyfikuje go, `fenv_access` musi być włączony przez `/fp:strict` opcję lub za pomocą `fenv_access` dyrektywy pragma, aby te funkcje miały efekt. Gdy `fenv_access` nie jest włączona, dostęp lub modyfikacja środowiska zmiennoprzecinkowego może skutkować nieoczekiwanym zachowaniem programu: kod może nie honorować żądanych zmian w środowisku zmiennoprzecinkowym; rejestry stanu zmiennoprzecinkowego mogą nie zgłaszać oczekiwanych lub bieżących wyników; w przeciwnym razie mogą wystąpić wyjątki zmiennoprzecinkowe lub oczekiwane mogą być wyjątki zmiennoprzecinkowe.

Gdy kod uzyskuje dostęp do środowiska zmiennoprzecinkowego lub modyfikuje go, należy zachować ostrożność podczas łączenia kodu, gdzie `fenv_access` jest włączona z kodem, który nie został `fenv_access` włączony. W kodzie, w którym `fenv_access` nie jest włączony, kompilator zakłada, że środowisko zmiennoprzecinkowe platformy działa domyślnie i że stan zmiennoprzecinkowy nie jest dostępny ani modyfikowany. Zalecamy zapisanie i przywrócenie lokalnego środowiska zmiennoprzecinkowego do stanu domyślnego przed przekazaniem kontroli do funkcji, która nie została `fenv_access` włączona. W tym przykładzie pokazano, jak `float_control` można ustawić i przywrócić pragma:

```cpp
#pragma float_control(strict, on, push)
// Code that uses /fp:strict mode
#pragma float_control(pop)
```

### <a name="floating-point-rounding-modes"></a>Tryby zaokrąglania liczb zmiennoprzecinkowych

W obu `/fp:precise` i `/fp:fast` kompilator generuje kod przeznaczony do uruchamiania w domyślnym środowisku zmiennoprzecinkowym i zakłada, że środowisko nie jest dostępne ani modyfikowane w czasie wykonywania. Oznacza to, że założono, że kod nie rozmaskuje wyjątków zmiennoprzecinkowych, odczytuje lub zapisuje rejestry stanu zmiennoprzecinkowego lub zmienia tryby zaokrąglania.  Jednak niektóre programy muszą zmienić środowisko zmiennoprzecinkowe. Na przykład ten przykład służy do obliczania powiązań zmiennoprzecinkowych, zmieniając tryby zaokrąglania zmiennoprzecinkowego:

```cpp
// fp_error_bounds.cpp
#include <iostream>
#include <limits>
using namespace std;

int main(void)
{
    float a = std::<float>::max();
    float b = -1.1;
    float cLower = 0.0;
    float cUpper = 0.0;
    unsigned int control_word = 0;
    int err = 0;

    // compute lower error bound.
    // set rounding mode to -infinity.
    err = _controlfp_s(&control_word, _RC_DOWN, _MCW_RC);
    if (err)
    {
        cout << "_controlfp_s(&control_word, _RC_DOWN, _MCW_RC) failed with error:" << err << endl;
    }  
    cLower = a * b;

    // compute upper error bound.
    // set rounding mode to +infinity.
    err = _controlfp_s(&control_word, _RC_UP, _MCW_RC);
    if (err)
    {
        cout << "_controlfp_s(&control_word, _RC_UP, _MCW_RC) failed with error:" << err << endl;
    }
    cUpper = a * b;

    // restore default rounding mode.
    err = _controlfp_s(&control_word, _CW_DEFAULT, _MCW_RC);
    if (err)
    {
        cout << "_controlfp_s(&control_word, _CW_DEFAULT, _MCW_RC) failed with error:" << err << endl;
    }
    // display error bounds.
    cout << "cLower = " << cLower << endl;
    cout << "cUpper = " << cUpper << endl;
    return 0;
}
```

Ponieważ kompilator zakłada, że domyślne środowisko zmiennoprzecinkowe w obszarze `/fp:fast` i `/fp:precise` jest wolne do ignorowania wywołań do `_controlfp_s` . Na przykład podczas kompilowania przy użyciu obu `/O2` i `/fp:precise` dla architektury x86 granice nie są obliczane, a przykładowe dane wyjściowe programu:

```Output
cLower = -inf
cUpper = -inf
```

Po skompilowaniu z `/O2` i `/fp:strict` dla architektury x86, dane wyjściowe programu przykładowe:

```Output
cLower = -inf
cUpper = -3.40282e+38
```

### <a name="floating-point-special-values"></a>Wartości specjalne zmiennoprzecinkowe

W obszarze `/fp:precise` i `/fp:strict` , wyrażenia obejmujące specjalne wartości (NaN, + nieskończoność, nieskończoność,-0,0) zachowują się zgodnie ze specyfikacjami IEEE-754. W obszarze `/fp:fast` , zachowanie tych specjalnych wartości może być niespójne z IEEE-754.

Ten przykład ilustruje różne zachowanie specjalnych wartości w `/fp:precise` `/fp:strict` i `/fp:fast` :

```cpp
// fp_special_values.cpp
#include <stdio.h>
#include <cmath>

float gf0 = -0.0;

int main()
{
    float f1 = INFINITY;
    float f2 = NAN;
    float f3 = -INFINITY;
    bool a, b;
    float c, d, e;
    a = (f1 == f1);
    b = (f2 == f2);
    c = (f1 - f1);
    d = (f2 - f2);
    printf("INFINITY == INFINITY : %d\n", a);
    printf("NAN == NAN           : %d\n", b);
    printf("INFINITY - INFINITY  : %f\n", c);
    printf("NAN - NAN            : %f\n", d);

    e = gf0 / abs(f3);
    printf("std::signbit(-0.0/-INFINITY): %d\n", std::signbit(c));
    return 0;
}
```

W przypadku kompilowania z `/O2` `/fp:precise` lub `/O2` `/fp:strict` dla architektury x86 dane wyjściowe są zgodne ze specyfikacją IEEE-754:

```Output
INFINITY == INFINITY : 1
NAN == NAN           : 0
INFINITY - INFINITY  : -nan(ind)
NAN - NAN            : -nan(ind)
std::signbit(-0.0/-INFINITY): 1
```

W przypadku kompilacji przy użyciu `/O2` `/fp:fast` dla architektury x86 dane wyjściowe nie są spójne z IEEE-754:

```Output
INFINITY == INFINITY : 1
NAN == NAN           : 1
INFINITY - INFINITY  : 0.000000
NAN - NAN            : 0.000000
std::signbit(-0.0/-INFINITY): 0
```

### <a name="floating-point-algebraic-transformations"></a>Przekształceń algebraicznych zmiennoprzecinkowych

W obszarze `/fp:precise` i `/fp:strict` , kompilator nie wykonuje transformacji matematycznych, chyba że transformacja jest gwarantowana w celu wygenerowania bitowego identycznego wyniku. Kompilator może wykonać takie przekształcenia w `/fp:fast` . Na przykład wyrażenie `a * b + a * c` w funkcji Sample `algebraic_transformation` może być kompilowane do poziomu `a * (b + c)` `/fp:fast` . Takie przekształcenia nie są wykonywane w ramach `/fp:precise` lub `/fp:strict` , a kompilator generuje `a * b + a * c` .

```cpp
float algebraic_transformation (float a, float b, float c)
{
    return a * b + a * c;
}
```

### <a name="floating-point-explicit-casting-points"></a>Jawne punkty rzutowania zmiennoprzecinkowego

W obszarze `/fp:precise` i `/fp:strict` , kompilator zaokrągla do dokładności kodu źródłowego w czterech określonych punktach podczas obliczania wyrażenia: na typecasts, gdy argument zmiennoprzecinkowy jest przesyłany do wywołania funkcji i gdy wartość zmiennoprzecinkowa jest zwracana z wywołania funkcji. Typecasts może służyć do jawnego zaokrąglania pośrednich obliczeń. W obszarze `/fp:fast` , kompilator nie generuje jawnych rzutowania w tych punktach w celu zagwarantowania dokładności kodu źródłowego. Ten przykład ilustruje zachowanie w różnych `/fp` opcjach:

```cpp
float casting(float a, float b)
{
    return 5.0*((double)(a+b));
}
```

Po skompilowaniu za pomocą `/O2` `/fp:precise` lub `/O2` `/fp:strict` można zobaczyć, że rzutowania typu jawnego są wstawiane zarówno w rzutowanie, jak i w punkcie powrotu funkcji w wygenerowanym kodzie dla architektury x64:

```asm
        addss    xmm0, xmm1
        cvtss2sd xmm0, xmm0
        mulsd    xmm0, QWORD PTR __real@4014000000000000
        cvtsd2ss xmm0, xmm0
        ret      0
```

W obszarze `/O2` `/fp:fast` wygenerowany kod jest uproszczony, ponieważ wszystkie rzutowania typu są zoptymalizowane:

```asm
        addss    xmm0, xmm1
        mulss    xmm0, DWORD PTR __real@40a00000
        ret      0
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Configuration Properties**  >  stronę właściwości konfiguracja generowania kodu**C/C++**  >  **Code Generation** .

1. Zmodyfikuj właściwość **modelu zmiennoprzecinkowego** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.floatingPointModel%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
