---
title: /FP (określenie zachowania zmiennoprzecinkowego)
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
ms.openlocfilehash: 25b228c16f534ca227d50bfdf632fdacb5703cd9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292358"
---
# <a name="fp-specify-floating-point-behavior"></a>/FP (określenie zachowania zmiennoprzecinkowego)

Określa, jak kompilator traktuje wyrażeń zmiennoprzecinkowych, optymalizacji i wyjątki. **/FP** opcje określają, czy wygenerowanego kodu umożliwia zmiennoprzecinkowych środowiska zmiany trybu zaokrąglania, maski wyjątku i subnormal zachowanie i tego, czy sprawdzanie stanu zmiennoprzecinkowego Zwraca bieżące, dokładne wyniki. Określa, czy kompilator generuje kod, który przechowuje operacja źródła i kolejność wyrażenia i jest zgodny ze standardem Propagacja NaN, lub jeśli zamiast tego generuje kod bardziej wydajne, który może zmienić kolejność lub operacje łączenia i użycia, co upraszcza algebraicznych przekształceń, które nie są dozwolone przez standard.

## <a name="syntax"></a>Składnia

> **/ FP:**[**dokładne** | **strict** | **szybkie** | **z wyjątkiem**[ **-**]]

### <a name="arguments"></a>Argumenty

#### <a name="precise"></a>dokładny

Domyślnie kompilator używa `/fp:precise` zachowanie.

W obszarze `/fp:precise` kompilator zachowuje wyrażenie źródłowe, kolejność i zaokrąglania właściwości kodu zmiennoprzecinkowego, gdy generuje i optymalizuje kod obiektowy dla docelowej maszyny. Kompilator powoduje zaokrąglenie do źródłowego dokładność kodu w określonych punktach w czterech podczas obliczania wyrażenia: u przypisania, w rzutowaniach typu, gdy argument zmiennoprzecinkowy jest przekazywany do wywołania funkcji i w przypadku, gdy wartość zmiennoprzecinkowa jest zwracana z wywołania funkcji. Pośrednich obliczeń mogą być wykonywane na maszynie dokładności. Rzutowaniach typu może służyć do jawnie zaokrąglenia pośrednich obliczeń.

Kompilator wykonuje przekształcenia algebraiczne zmiennoprzecinkowych wyrażeń, takie jak ponownego kojarzenia lub dystrybucji, dopiero po transformacji jest gwarantowane rezultatów bitowe identyczne.
Wyrażeniami, które zawierają specjalnych wartości (NaN, + nieskończoność, - nieskończoność,-0.0) są przetwarzane zgodnie z IEEE 754 specyfikacji. Na przykład `x != x` daje w wyniku **true** Jeśli x jest wartością typu NaN. Zmiennoprzecinkowe *skrótów*, oznacza to, że instrukcje maszynowe, które łączą operacji zmiennoprzecinkowych, mogą być generowane w taki sposób, w obszarze `/fp:precise`.

Kompilator generuje kod przeznaczony do uruchamiania [zmiennoprzecinkowych środowiska domyślnego](#the-default-floating-point-environment) i przyjęto założenie, że środowisko zmiennoprzecinkowe nie dostęp lub zmodyfikowany w czasie wykonywania. Oznacza to założono, że kod nie Anuluj maskowanie wyjątki zmiennoprzecinkowe, odczytu lub zapisu stanu zmiennoprzecinkowego rejestrów lub zmienić trybów zaokrąglania.

Jeśli kod zmiennoprzecinkowy nie zależy od kolejności operacji i wyrażenia w zestawienia zmiennoprzecinkowych (na przykład, jeśli nie dba czy `a * b + a * c` jest obliczana jako `(b + c) * a` lub `2 * a` jako `a + a`), należy wziąć pod uwagę [Fast](#fast) opcja, która może tworzyć kod szybciej i bardziej wydajne. Jeśli Twój kod zarówno zależy od kolejności działań i wyrażeń i uzyskuje dostęp do lub zmienia zmiennoprzecinkowych środowisku (na przykład, aby zmienić tryb zaokrąglania lub przechwytują wyjątki zmiennoprzecinkowe), użyj [/FP: strict](#strict).

#### <a name="strict"></a>ściśle

`/fp:strict` ma zachowanie podobne do `/fp:precise`, oznacza to, kompilator zachowuje kolejności źródła i zaokrąglania właściwości kodu zmiennoprzecinkowego, gdy generuje i optymalizuje obiektów kodu dla docelowej maszyny i przestrzega standardowej podczas obsługi specjalnych wartości. Ponadto program może bezpiecznie dostępu lub modyfikacji zmiennoprzecinkowych środowiska w czasie wykonywania.

W obszarze `/fp:strict`, kompilator generuje kod, który umożliwia programowi bezpiecznie maskowanie wyjątki zmiennoprzecinkowe, odczytać lub zapisać stanu zmiennoprzecinkowego rejestrów lub zmienić trybów zaokrąglania. Zaokrągla liczbę do źródłowego dokładność kodu w określonych punktach w czterech podczas obliczania wyrażenia: u przypisania, w rzutowaniach typu, gdy argument zmiennoprzecinkowy jest przekazywany do wywołania funkcji i w przypadku, gdy wartość zmiennoprzecinkowa jest zwracana z wywołania funkcji. Pośrednich obliczeń mogą być wykonywane na maszynie dokładności. Rzutowaniach typu może służyć do jawnie zaokrąglenia pośrednich obliczeń. Kompilator wykonuje przekształcenia algebraiczne zmiennoprzecinkowych wyrażeń, takie jak ponownego kojarzenia lub dystrybucji, dopiero po transformacji jest gwarantowane rezultatów bitowe identyczne. Wyrażeniami, które zawierają specjalnych wartości (NaN, + nieskończoność, - nieskończoność,-0.0) są przetwarzane zgodnie z IEEE 754 specyfikacji. Na przykład `x != x` daje w wyniku **true** Jeśli x jest wartością typu NaN. Skrótów zmiennoprzecinkowe nie są generowane w `/fp:strict`.

`/fp:strict` jest obliczeniowo bardziej kosztowne niż `/fp:precise` ponieważ kompilator należy wstawić dodatkowe instrukcje przechwytują wyjątki i Zezwalaj na dostęp lub zmodyfikować zmiennoprzecinkowych środowiska w czasie wykonywania programów. Jeśli Twój kod nie używać tej funkcji, ale wymaga porządkowanie kodu źródłowego i zaokrąglania lub zależy od specjalnych wartości, użyj `/fp:precise`. W przeciwnym razie należy wziąć pod uwagę przy użyciu `/fp:fast`, które mogą wygenerować szybszy i mniejszy kod.

#### <a name="fast"></a>Szybka

`/fp:fast` Opcja umożliwia kompilator, aby zmienić kolejność, połączyć lub Uprość operacji zmiennoprzecinkowych, aby zoptymalizować kod zmiennoprzecinkowy szybkość i najlepsze miejsce. Kompilator może pominąć Zaokrąglenie w instrukcjach przypisania, rzutowaniach typu lub wywołaniach funkcji. Może zmienić kolejność operacji lub wykonywać przekształcenia algebraiczne, na przykład przy użyciu łączności i rozdzielności przepisów, nawet jeśli takie przekształcenia spowodować ciemniejsza różne zachowanie zaokrąglania. Ze względu na tego rodzaju optymalizacji rozszerzone, wynik kilka obliczeń zmiennoprzecinkowych może różnić się od wyprodukowane przez inne `/fp` opcje. Specjalnych wartości (NaN, + nieskończoność, - nieskończoność,-0.0) nie można propagować lub zachowywać się wyłącznie zgodnie ze standardem IEEE-754. Zmiennoprzecinkowe skrótów mogą być generowane w obszarze `/fp:fast`. Kompilator jest nadal powiązane przez podstawową architekturę, w obszarze `/fp:fast`, i dodatkowe optymalizacje mogą być dostępne za pośrednictwem [/arch](arch-minimum-cpu-architecture.md) opcji.

W obszarze `/fp:fast`, kompilator generuje kod przeznaczony do uruchamiania w domyślnym środowisku zmiennoprzecinkowe i przyjęto założenie, że zmiennoprzecinkowych środowisko nie jest dostępne lub zmodyfikowany w czasie wykonywania. Oznacza to założono, że kod nie Anuluj maskowanie wyjątki zmiennoprzecinkowe, odczytu lub zapisu stanu zmiennoprzecinkowego rejestrów lub zmienić trybów zaokrąglania.

`/fp:fast` jest przeznaczony dla programów, które nie wymagają kodu źródłowego strict, kolejność i zaokrąglania wyrażeń liczb zmiennopozycyjnych i nie należy polegać na standardowe reguły do obsługi specjalnych wartości, takich jak NaN. Jeśli kod zmiennoprzecinkowy wymaga zachowania kodu źródłowego, kolejność i zaokrąglania lub opiera się na standardowe zachowanie specjalnych wartości, użyj [/FP: precise](#precise). Jeśli kod uzyskuje dostęp do lub modyfikuje zmiennoprzecinkowych środowiska, aby zmienić tryb zaokrąglania, anulować maskowanie wyjątków zmiennoprzecinkowych, lub Sprawdź stan zmiennoprzecinkowego, użyj [/FP: strict](#strict).

#### <a name="except"></a>Z wyjątkiem

`/fp:except` Opcja generuje kod, aby zapewnia, że wszelkie zaznaczona wyjątki zmiennoprzecinkowe są wywoływane w dokładny moment, w którym występują one i, nie dodatkowe wyjątki zmiennoprzecinkowe są wywoływane. Domyślnie `/fp:strict` opcji umożliwia `/fp:except`, i `/fp:precise` nie. `/fp:except` Opcja nie jest zgodny z `/fp:fast`. Opcja można jawnie wyłączone przez nas o `/fp:except-`.

Należy pamiętać, że `/fp:except` nie włącza wyjątki zmiennoprzecinkowe przez siebie, ale jest to wymagane dla programów włączyć wyjątki zmiennoprzecinkowe. Zobacz [_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md) informacji o sposobie włączania wyjątki zmiennoprzecinkowe.

## <a name="remarks"></a>Uwagi

Wiele `/fp` opcje można określić w tym samym wierszu polecenia kompilatora. Tylko jeden z `/fp:strict`, `/fp:fast`, i `/fp:precise` opcji może być wdrożony w naraz. Jeśli więcej niż jedną z tych opcji jest określony w wierszu polecenia, nowsze opcji ma pierwszeństwo, a kompilator generuje ostrzeżenie. `/fp:strict` i `/fp:except` opcje nie są zgodne z `/clr`.

[/Za](za-ze-disable-language-extensions.md) opcji (zgodność z ANSI) nie jest zgodny z `/fp`.

### <a name="using-compiler-directives-to-control-floating-point-behavior"></a>Aby kontrolować zachowanie liczb zmiennopozycyjnych za pomocą dyrektywy kompilatora

Kompilator udostępnia trzy dyrektyw pragma, aby zastąpić zachowanie liczb zmiennopozycyjnych, określone w wierszu polecenia: [float_control](../../preprocessor/float-control.md), [fenv_access](../../preprocessor/fenv-access.md), i [fp_contract](../../preprocessor/fp-contract.md). Te dyrektywy umożliwia kontrolować zachowanie liczb zmiennopozycyjnych na poziomie funkcji, nie w obrębie danej funkcji. Należy pamiętać, że te dyrektywy nie odpowiadają bezpośrednio do `/fp` opcje. W poniższej tabeli przedstawiono sposób, w jaki `/fp` opcje i dyrektyw pragma mapowanie między sobą. Aby uzyskać więcej informacji zobacz dokumentację poszczególne opcje i dyrektyw pragma.

||float_control(Precise)|float_control(EXCEPT)|fenv_access|fp_contract|
|-|-|-|-|-|
|`/fp:fast`|wyłączone|wyłączone|wyłączone|on|
|`/fp:precise`|on|wyłączone|wyłączone|on|
|`/fp:strict`|on|on|on|wyłączone|

### <a name="the-default-floating-point-environment"></a>Domyślne środowisko punktu zmiennoprzecinkowego

Po zainicjowaniu procesu *domyślnego środowiska punktu zmiennoprzecinkowego* jest ustawiona. To środowisko maskuje wyjątki zmiennoprzecinkowe wszystkie, ustawia tryb zaokrąglania zaokrąglić do najbliższej (`FE_TONEAREST`), zachowuje subnormal (zdenormalizowany) wartości, domyślna precyzja mantysę (mantysy) używa **float**, **double**, i **typu long double** wartości, a jeśli są obsługiwane, ustawia formant nieskończoność, domyślny tryb przekształceniem afinicznym.

### <a name="floating-point-environment-access-and-modification"></a>Dostęp do środowiska zmiennoprzecinkowe i jego modyfikacji

Środowisko uruchomieniowe Microsoft Visual C++ udostępnia kilka funkcji zmiennoprzecinkowej środowiska modyfikacji i dostępu do. Obejmują one [_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md), [_clearfp —](../../c-runtime-library/reference/clear87-clearfp.md), i [_statusfp —](../../c-runtime-library/reference/status87-statusfp-statusfp2.md) i ich odmian. Aby zapewnić zachowanie odpowiedniego programu, gdy kod uzyskuje dostęp do lub modyfikuje zmiennoprzecinkowych środowiska `fenv_access` musi być włączony, albo przez `/fp:strict` opcji lub poprzez użycie `fenv_access` pragma dla tych funkcji mieć żadnego efektu. Gdy `fenv_access` jest nie jest włączone, dostępu lub modyfikacji zmiennoprzecinkowych środowiska może spowodować nieoczekiwane program zachowanie: kod może nie uznaje zlecone zmiany dotyczące środowiska zmiennoprzecinkowych; rejestrów zmiennoprzecinkowych stanu mogą nie zgłaszać Oczekiwano lub bieżące wyniki; mogą wystąpić nieoczekiwane wyjątki zmiennoprzecinkowe i oczekiwane wyjątki zmiennoprzecinkowe mogą nie być wykrywane.

Gdy kod uzyskuje dostęp do lub modyfikuje zmiennoprzecinkowych środowiska, należy zachować ostrożność podczas łączenia kodu gdzie `fenv_access` jest włączone z kodem, który nie ma `fenv_access` włączone. W kodzie gdzie `fenv_access` nie jest włączone, kompilator zakłada, czy domyślne środowisko zmiennoprzecinkowych platformy jest aktywna i czy stanu zmiennoprzecinkowego nie jest otwierane ani modyfikowane. Zalecamy zapisywanie i przywracanie lokalnego środowiska zmiennoprzecinkowych do stanu domyślnego, zanim sterowanie jest przekazywane do funkcji, która nie ma `fenv_access` włączone. W tym przykładzie przedstawiono sposób, w jaki `float_control` pragma można ustawić i przywrócone:

```cpp
#pragma float_control(strict, on, push)
// Code that uses /fp:strict mode
#pragma float_control(pop)
```

### <a name="floating-point-rounding-modes"></a>Zmiennoprzecinkowe trybów zaokrąglania

W obszarze zarówno `/fp:precise` i `/fp:fast` kompilator generuje kod przeznaczony do uruchamiania w domyślnym środowisku zmiennoprzecinkowe i przyjęto założenie, że środowisko nie jest dostępny lub zmodyfikowany w czasie wykonywania. Oznacza to założono, że kod nie Anuluj maskowanie wyjątki zmiennoprzecinkowe, odczytu lub zapisu stanu zmiennoprzecinkowego rejestrów lub zmienić trybów zaokrąglania.  Jednak niektóre programy, należy zmodyfikować środowisko zmiennoprzecinkowych. Na przykład w tym przykładzie oblicza granice błąd zmiennoprzecinkowych mnożenia przez zmianę trybów zaokrąglania zmiennoprzecinkowa:

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

Ponieważ kompilator zakłada domyślne liczb zmiennoprzecinkowych środowiska punktu, w obszarze `/fp:fast` i `/fp:precise` to bezpłatne ignorować wywołania do `_controlfp_s`. Na przykład, gdy kompilowany przy użyciu zarówno `/O2` i `/fp:precise` dla x86 architektury, granice nie są obliczane i program przykładowe dane wyjściowe:

```Output
cLower = -inf
cUpper = -inf
```

Gdy skompilowano z opcją zarówno `/O2` i `/fp:strict` dla x86 architektury, przykładowy program wyświetla:

```Output
cLower = -inf
cUpper = -3.40282e+38
```

### <a name="floating-point-special-values"></a>Wartości zmiennoprzecinkowe specjalne

W obszarze `/fp:precise` i `/fp:strict`, wyrażeniami, które zawierają specjalnych wartości (NaN, + nieskończoność, - nieskończoność,-0.0) zachowują się zgodnie z IEEE 754 specyfikacji. W obszarze `/fp:fast`, zachowanie tych specjalnych wartości mogą być niezgodne z IEEE 754.

W tym przykładzie pokazano odmienne zachowanie specjalnych wartości w obszarze `/fp:precise`, `/fp:strict` i `/fp:fast`:

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

Gdy skompilowano z opcją `/O2` `/fp:precise` lub `/O2` `/fp:strict` dla x86 architektury, dane wyjściowe są zgodne ze specyfikacją IEEE 754:

```Output
INFINITY == INFINITY : 1
NAN == NAN           : 0
INFINITY - INFINITY  : -nan(ind)
NAN - NAN            : -nan(ind)
std::signbit(-0.0/-INFINITY): 1
```

Gdy skompilowano z opcją `/O2` `/fp:fast` dla x86 architektury, dane wyjściowe nie są zgodne z IEEE 754:

```Output
INFINITY == INFINITY : 1
NAN == NAN           : 1
INFINITY - INFINITY  : 0.000000
NAN - NAN            : 0.000000
std::signbit(-0.0/-INFINITY): 0
```

### <a name="floating-point-algebraic-transformations"></a>Przekształcenia algebraiczne zmiennoprzecinkowych

W obszarze `/fp:precise` i `/fp:strict`, kompilator wykonuje matematyczne przekształcenia dopiero po transformacji jest gwarantowane rezultatów bitowe identyczne. Kompilator może wykonywać takie przekształcenia w obszarze `/fp:fast`. Na przykład, wyrażenie `a * b + a * c` w wyświetlany kod przykładowej funkcji `algebraic_transformation` mogą być skompilowane w ramach `a * (b + c)` w obszarze `/fp:fast`. Takie przekształcenia nie są wykonywane w ramach `/fp:precise` lub `/fp:strict`, a kompilator generuje `a * b + a * c`.

```cpp
float algebraic_transformation (float a, float b, float c)
{
    return a * b + a * c;
}
```

### <a name="floating-point-explicit-casting-points"></a>Punkty zmiennoprzecinkowych jawnego rzutowania

W obszarze `/fp:precise` i `/fp:strict`, kompilator powoduje zaokrąglenie do źródłowego dokładność kodu w określonych punktach w czterech podczas obliczania wyrażenia: u przypisania, w rzutowaniach typu, gdy argument zmiennoprzecinkowy jest przekazywany do wywołania funkcji, a w przypadku liczb zmiennoprzecinkowych wartość jest zwracana z wywołania funkcji. Rzutowaniach typu może służyć do jawnie zaokrąglenia pośrednich obliczeń. W obszarze `/fp:fast`, kompilator nie generuje ma jawnych rzutowań w tych punktach, aby zagwarantować dokładności kodu źródłowego. Niniejszy przykład pokazuje zachowanie w różnych `/fp` opcje:

```cpp
float casting(float a, float b)
{
    return 5.0*((double)(a+b));
}
```

Gdy kompilowany przy użyciu `/O2` `/fp:precise` lub `/O2` `/fp:strict`, możesz zobaczyć, że typu jawnego rzutowania są wstawiane w obu rzutowanie typu, jak i w punkcie zwrotu funkcji w wygenerowanym kodzie x64 architektury:

```asm
        addss    xmm0, xmm1
        cvtss2sd xmm0, xmm0
        mulsd    xmm0, QWORD PTR __real@4014000000000000
        cvtsd2ss xmm0, xmm0
        ret      0
```

W obszarze `/O2` `/fp:fast` wygenerowany kod jest uproszczony, ponieważ wszystkie rzutowania typów są optymalizacji:

```asm
        addss    xmm0, xmm1
        mulss    xmm0, DWORD PTR __real@40a00000
        ret      0
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **generowania kodu** stronę właściwości.

1. Modyfikowanie **Model zmiennoprzecinkowy** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.floatingPointModel%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
