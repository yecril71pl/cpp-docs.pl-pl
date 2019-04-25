---
title: Obsługa złożonych obliczeń w języku C
ms.date: 03/30/2018
f1_keywords:
- c.complex
helpviewer_keywords:
- complex numbers, math routines
- math routines
- complex numbers
ms.openlocfilehash: 12ba858993d3712cbf390288df60faedc602c90a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62290017"
---
# <a name="c-complex-math-support"></a>Obsługa złożonych obliczeń w języku C

Biblioteka Microsoft C Runtime (CRT) zapewnia funkcje biblioteki złożonych obliczeń, wraz ze wszystkimi wymaganymi przez ISO C99. Kompilator nie obsługuje bezpośrednio **złożonych** lub **_complex —** — słowo kluczowe, w związku z tym implementacja firmy Microsoft korzysta z typów struktury do reprezentowania liczb zespolonych.

Te funkcje są implementowane aby zrównoważyć wydajność za pomocą poprawności. Ponieważ tworzenie poprawnie zaokrąglony wynik może być zbyt duży, te funkcje są przeznaczone do wydajnego tworzenia bliskie zbliżenia wyniku poprawnie zaokrąglony. W większości przypadków wynik tworzony mieści się w +/-1 ulp poprawnie zaokrąglone wyniku, chociaż może się zdarzyć, gdy większej dokładności.

Procedury matematyczne złożonych zależą od tego, wartość zmiennoprzecinkowa punktu funkcji bibliotek matematycznych ich wdrażania. Funkcje te mają różne implementacje dla innej architektury Procesora. Na przykład x86 32-bitowych CRT może mieć inną implementację od x64 64-bitowych CRT. Ponadto niektóre funkcje mogą mieć wiele implementacji dla danej architektury Procesora. Najbardziej efektywny sposób wdrażania jest wybierana dynamicznie w czasie wykonywania w zależności od zestawów instrukcji, obsługiwanych przez CPU. Na przykład w x86 32-bitowych CRT, niektóre funkcje mają zarówno x87 implementacji i implementację SSE2. Podczas uruchamiania, na którego procesor CPU obsługuje SSE2, szybsze implementacji SSE2 jest używany. Podczas uruchamiania na procesorze CPU, który nie obsługuje SSE2, wolniejsze x87 implementacja jest używana. Ponieważ różne implementacje funkcji bibliotek matematycznych może używać różne instrukcje procesora CPU i różnych algorytmów, aby wygenerować ich wyniki, funkcje mogą wygenerować różne wyniki we wszystkich procesorach. W większości przypadków wyniki znajdują się w +/-1 ulp poprawnie zaokrąglone wyników, ale rzeczywiste wyniki mogą się różnić we wszystkich procesorach.

## <a name="types-used-in-complex-math"></a>Typy używane w złożonych obliczeń

Implementacja firmy Microsoft w nagłówku complex.h definiuje te typy jako odpowiedniki C99 standardowych natywnych złożonych typów:

|Standardowe|Typ firmy Microsoft|
|-|-|
|**złożone float** lub **float _complex —**|**_FComplex**|
|**podwójne złożone** lub **double _complex —**|**_DComplex**|
|**złożone typu Long double** lub **_complex typu long double —**|**_LComplex**|

W nagłówku math.h definiuje oddzielnego typu **_complex — struktura**, który jest używany dla [_cabs](../c-runtime-library/reference/cabs.md) funkcji. **_Complex — struktura** typu nie jest używany przez równoważne złożone funkcje matematyczne [pliki cab, cabsf cabsl —](../c-runtime-library/reference/cabs-cabsf-cabsl.md).

## <a name="complex-constants-and-macros"></a>Złożone stałe i makra

**Czy mogę** jest zdefiniowany jako **float** typu złożonego **_FComplex** inicjowane przez `{ 0.0f, 1.0f }`.

## <a name="trigonometric-functions"></a>Funkcje trygonometryczne

|Funkcja|Opis|
|-|-|
|[cacos, cacosf, cacosl](../c-runtime-library/reference/cacos-cacosf-cacosl.md)|Obliczenia złożonych funkcji arcus cosinus liczby zespolonej|
|[casin, casinf, casinl](../c-runtime-library/reference/casin-casinf-casinl.md)|Obliczenia złożonych funkcji arcus sinus liczby zespolonej|
|[catan, catanf, catanl](../c-runtime-library/reference/catan-catanf-catanl.md)|Obliczenia złożonych funkcji arcus tangens liczby zespolonej|
|[ccos, ccosf, ccosl](../c-runtime-library/reference/ccos-ccosf-ccosl.md)|Obliczenia złożonych cosinus liczby zespolonej|
|[csin, csinf, csinl](../c-runtime-library/reference/csin-csinf-csinl.md)|Obliczenia złożonych sinus liczby zespolonej|
|[ctan, ctanf, ctanl](../c-runtime-library/reference/ctan-ctanf-ctanl.md)|Obliczenia złożonych tangens liczby zespolonej|

## <a name="hyperbolic-functions"></a>Funkcje hiperboliczne

|Funkcja|Opis|
|-|-|
|[cacosh, cacoshf, cacoshl](../c-runtime-library/reference/cacosh-cacoshf-cacoshl.md)|Obliczenia złożonych arcus cosinus hiperboliczny liczby zespolonej|
|[casinh, casinhf, casinhl](../c-runtime-library/reference/casinh-casinhf-casinhl.md)|Obliczenia złożonych arcus sinus hiperboliczny liczby zespolonej|
|[catanh, catanhf, catanhl](../c-runtime-library/reference/catanh-catanhf-catanhl.md)|Obliczenia złożonych arcus tangens hiperboliczny liczby zespolonej|
|[ccosh, ccoshf, ccoshl](../c-runtime-library/reference/ccosh-ccoshf-ccoshl.md)|Obliczenia złożonych cosinus hiperboliczny dla liczby zespolonej|
|[csinh, csinhf, csinhl](../c-runtime-library/reference/csinh-csinhf-csinhl.md)|Obliczenia złożonych sinus hiperboliczny liczby zespolonej|
|[ctanh, ctanhf, ctanhl](../c-runtime-library/reference/ctanh-ctanhf-ctanhl.md)|Obliczenia złożonych tangens hiperboliczny dla liczby zespolonej|

## <a name="exponential-and-logarithmic-functions"></a>Funkcji wykładniczej i logarytmiczną

|Funkcja|Opis|
|-|-|
|[cexp, cexpf, cexpl](../c-runtime-library/reference/cexp-cexpf-cexpl.md)|Obliczenia złożone podstawowej -*e* wykładniczą liczby zespolonej|
|[clog, clogf, clogl](../c-runtime-library/reference/clog-clogf-clogl.md)|Obliczenia złożonych naturalnego (podstawowy -*e*) logarytm liczby zespolonej|
|[clog10, clog10f, clog10l](../c-runtime-library/reference/clog10-clog10f-clog10l.md)|Obliczenia złożonych logarytm o podstawie base 10 liczby zespolonej|

## <a name="power-and-absolute-value-functions"></a>Możliwości i funkcje wartość bezwzględna

|Funkcja|Opis|
|-|-|
|[cabs, cabsf, cabsl](../c-runtime-library/reference/cabs-cabsf-cabsl.md)|Obliczenia złożona wartość bezwzględna (nazywane również norm, modułu lub wielkości) liczby zespolonej|
|[cpow, cpowf, cpowl](../c-runtime-library/reference/cpow-cpowf-cpowl.md)|Obliczenia funkcji power złożonych x<sup>y</sup>|
|[csqrt, csqrtf, csqrtl](../c-runtime-library/reference/csqrt-csqrtf-csqrtl.md)|Obliczenia złożonych pierwiastek kwadratowy liczby zespolonej|

## <a name="manipulation-functions"></a>Funkcje manipulowania

|Funkcja|Opis|
|-|-|
|[_Cbuild, _FCbuild, _LCbuild](../c-runtime-library/reference/cbuild-fcbuild-lcbuild.md)|Konstrukcja z rzeczywiste i urojone części liczby zespolonej|
|[carg, cargf, cargl](../c-runtime-library/reference/carg-cargf-cargl.md)|Obliczenia argumentu (nazywane również kąt fazy) liczby zespolonej|
|[cimag, cimagf, cimagl](../c-runtime-library/reference/cimag-cimagf-cimagl.md)|Obliczenia urojone części liczby zespolonej|
|[conj, conjf, conjl](../c-runtime-library/reference/conj-conjf-conjl.md)|Obliczenia zespolonej liczby zespolonej|
|[cproj, cprojf, cprojl](../c-runtime-library/reference/cproj-cprojf-cprojl.md)|Obliczenia projekcji sphere Riemanna liczby zespolonej|
|[creal, crealf, creall](../c-runtime-library/reference/creal-crealf-creall.md)|Obliczenia rzeczywistych część liczby zespolonej|
|[norm, normf, norml](../c-runtime-library/reference/norm-normf-norml1.md)|Obliczanie kwadratów wielkości liczby zespolonej|

## <a name="operation-functions"></a>Funkcje operacji

Ponieważ liczby zespolone nie są typu natywnego w kompilatorze Microsoft, standardowe operatory arytmetyczne nie są zdefiniowane dla typów złożonych. Dla wygody te funkcje biblioteki złożonych obliczeń umożliwiające manipulowanie ograniczonej liczby zespolone w kodzie użytkownika:

|Funkcja|Opis|
|-|-|
|[_Cmulcc, _FCmulcc, _LCmulcc](../c-runtime-library/reference/cmulcc-fcmulcc-lcmulcc.md)|Mnożenie dwóch liczb zespolonych|
|[_Cmulcr, _FCmulcr, _LCmulcr](../c-runtime-library/reference/cmulcr-fcmulcr-lcmulcr.md)|Pomnóż złożony i liczba zmiennoprzecinkowa|

## <a name="see-also"></a>Zobacz także

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
