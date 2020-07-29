---
title: Kompleksowe wsparcie matematyczne języka C
ms.date: 05/14/2019
f1_keywords:
- c.complex
helpviewer_keywords:
- complex numbers, math routines
- math routines
- complex numbers
ms.openlocfilehash: dac032940ed9d96764b64809c5f8901ac273898b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215182"
---
# <a name="c-complex-math-support"></a>Kompleksowe wsparcie matematyczne języka C

Biblioteka środowiska uruchomieniowego Microsoft C (CRT) oferuje złożone funkcje biblioteki matematycznej, w tym wszystkie wymagane przez C99 ISO. Kompilator nie obsługuje bezpośrednio **`complex`** **`_Complex`** słowa kluczowego or, dlatego implementacja firmy Microsoft używa typów struktury do reprezentowania liczb złożonych.

Te funkcje są implementowane w celu zrównoważenia wydajności z korekcją. Ponieważ generowanie prawidłowo zaokrąglonego wyniku może być niezwykle kosztowne, te funkcje są zaprojektowane w celu wydajnego utworzenia bliskiego przybliżenia do prawidłowo zaokrąglonego wyniku. W większości przypadków powstaje wynik w zakresie od +/-1 ULP prawidłowo zaokrąglonego wyniku, chociaż mogą wystąpić sytuacje, w których występuje większa niedokładność.

Złożone procedury matematyczne opierają się na funkcjach matematycznych w liczbie zmiennoprzecinkowych dla ich implementacji. Te funkcje mają różne implementacje dla różnych architektur procesora. Na przykład 32-bitowa architektura x86 CRT może mieć inną implementację niż 64-bit x64 CRT. Ponadto niektóre funkcje mogą mieć wiele implementacji dla danej architektury procesora CPU. Najbardziej wydajna implementacja jest wybierana dynamicznie w czasie wykonywania w zależności od zestawów instrukcji obsługiwanych przez procesor CPU. Na przykład w 32-bitowej architekturze x86, niektóre funkcje mają implementację x87 i implementację SSE2. W przypadku uruchamiania na PROCESORze, który obsługuje SSE2, używana jest szybsza implementacja SSE2. W przypadku uruchamiania na PROCESORze, który nie obsługuje SSE2, używana jest wolniejsza implementacja x87. Ponieważ różne implementacje funkcji biblioteki matematycznej mogą korzystać z różnych instrukcji procesora CPU i różnych algorytmów w celu wygenerowania ich wyników, funkcje mogą generować różne wyniki w procesorach. W większości przypadków wyniki znajdują się w przedziale od +/-1 ULP prawidłowo zaokrąglonego wyniku, ale rzeczywiste wyniki mogą się różnić w zależności od procesorów.

## <a name="types-used-in-complex-math"></a>Typy używane w złożonej matematycznej

Implementacja firmy Microsoft dla złożonego nagłówka. h definiuje te typy jako odpowiedniki dla natywnych typów C99 standardowych:

|Typ standardowy|Typ firmy Microsoft|
|-|-|
|**`float complex`** oraz**`float _Complex`**|**_Fcomplex**|
|**`double complex`** oraz**`double _Complex`**|**_Dcomplex**|
|**`long double complex`** oraz**`long double _Complex`**|**_Lcomplex**|

Nagłówek Math. h definiuje oddzielny typ **_complex struktury**używany przez funkcję [_cabs](../c-runtime-library/reference/cabs.md) . Typ **_complex struktury** nie jest używany przez równoważne złożone skomplikowane funkcje matematyczne [OOZ, cabsf, CAB](../c-runtime-library/reference/cabs-cabsf-cabsl.md).

## <a name="complex-constants-and-macros"></a>Złożone stałe i makra

**I** został zdefiniowany jako typ złożony **_Fcomplex** zainicjowany przez `{ 0.0f, 1.0f }` .

## <a name="trigonometric-functions"></a>Funkcje trygonometryczne

|Funkcja|Opis|
|-|-|
|[cacos, cacosf, cacosl](../c-runtime-library/reference/cacos-cacosf-cacosl.md)|Oblicz cosinus złożonego łuku dla liczby zespolonej|
|[casin, casinf, casinl](../c-runtime-library/reference/casin-casinf-casinl.md)|Oblicz łuk złożonego łuku dla liczby zespolonej|
|[catan, catanf, catanl](../c-runtime-library/reference/catan-catanf-catanl.md)|Oblicz skomplikowany tangens łuku liczby zespolonej|
|[ccos, ccosf, ccosl](../c-runtime-library/reference/ccos-ccosf-ccosl.md)|Oblicz skomplikowany cosinus liczby zespolonej|
|[csin, csinf, csinl](../c-runtime-library/reference/csin-csinf-csinl.md)|Oblicz skomplikowany sinus liczby zespolonej|
|[ctan, ctanf, ctanl](../c-runtime-library/reference/ctan-ctanf-ctanl.md)|Oblicz skomplikowany tangens liczby zespolonej|

## <a name="hyperbolic-functions"></a>Funkcje hiperboliczne

|Funkcja|Opis|
|-|-|
|[cacosh, cacoshf, cacoshl](../c-runtime-library/reference/cacosh-cacoshf-cacoshl.md)|Oblicz skomplikowany cosinus hiperboliczny liczby zespolonej|
|[casinh, casinhf, casinhl](../c-runtime-library/reference/casinh-casinhf-casinhl.md)|Oblicz złożone arcus sinus hiperboliczny liczby zespolonej|
|[catanh, catanhf, catanhl](../c-runtime-library/reference/catanh-catanhf-catanhl.md)|Oblicz złożony tangens hiperboliczny liczby zespolonej|
|[ccosh, ccoshf, ccoshl](../c-runtime-library/reference/ccosh-ccoshf-ccoshl.md)|Oblicz skomplikowany cosinus hiperboliczny liczby zespolonej|
|[csinh, csinhf, csinhl](../c-runtime-library/reference/csinh-csinhf-csinhl.md)|Oblicz skomplikowany sinus hiperboliczny liczby zespolonej|
|[ctanh, ctanhf, ctanhl](../c-runtime-library/reference/ctanh-ctanhf-ctanhl.md)|Oblicz skomplikowany tangens hiperboliczny liczby zespolonej|

## <a name="exponential-and-logarithmic-functions"></a>Funkcje wykładnicze i logarytmiczne

|Funkcja|Opis|
|-|-|
|[cexp, cexpf, cexpl](../c-runtime-library/reference/cexp-cexpf-cexpl.md)|Oblicz kompleksową liczbę wykładniczą-*e* w liczbie zespolonej|
|[clog, clogf, clogl](../c-runtime-library/reference/clog-clogf-clogl.md)|Oblicz skomplikowaną wartość logarytmu naturalnego (Base-*e*) liczby zespolonej|
|[clog10, clog10f, clog10l](../c-runtime-library/reference/clog10-clog10f-clog10l.md)|Oblicz złożony logarytm dziesiętny liczby zespolonej|

## <a name="power-and-absolute-value-functions"></a>Funkcje potęgowe i bezwzględne

|Funkcja|Opis|
|-|-|
|[cabs, cabsf, cabsl](../c-runtime-library/reference/cabs-cabsf-cabsl.md)|Oblicz złożoną wartość bezwzględną (zwaną również normą, modułem lub wielkością) liczby zespolonej|
|[cpow, cpowf, cpowl](../c-runtime-library/reference/cpow-cpowf-cpowl.md)|Oblicz złożoną funkcję potęgi x<sup>y</sup>|
|[csqrt, csqrtf, csqrtl](../c-runtime-library/reference/csqrt-csqrtf-csqrtl.md)|Oblicz zespolony pierwiastek kwadratowy z liczbą zespoloną|

## <a name="manipulation-functions"></a>Funkcje manipulowania

|Funkcja|Opis|
|-|-|
|[_Cbuild, _FCbuild, _LCbuild](../c-runtime-library/reference/cbuild-fcbuild-lcbuild.md)|Konstruowanie liczby zespolonej z części rzeczywistych i urojonych|
|[carg, cargf, cargl](../c-runtime-library/reference/carg-cargf-cargl.md)|Oblicza argument (nazywany również kątem fazy) liczby zespolonej|
|[cimag, cimagf, cimagl](../c-runtime-library/reference/cimag-cimagf-cimagl.md)|Oblicz część urojoną liczby zespolonej|
|[conj, conjf, conjl](../c-runtime-library/reference/conj-conjf-conjl.md)|Oblicz zespolone sprzężenie liczby zespolonej|
|[cproj, cprojf, cprojl](../c-runtime-library/reference/cproj-cprojf-cprojl.md)|Oblicz rzutowanie liczby zespolonej na Riemann sferę|
|[creal, crealf, creall](../c-runtime-library/reference/creal-crealf-creall.md)|Oblicz rzeczywistą część liczby zespolonej|
|[norm, normf, norml](../c-runtime-library/reference/norm-normf-norml1.md)|Oblicz kwadratową wielkość liczby zespolonej|

## <a name="operation-functions"></a>Funkcje operacji

Ponieważ liczby zespolone nie są typami natywnymi w kompilatorze firmy Microsoft, standardowe operatory arytmetyczne nie są zdefiniowane w typach złożonych. Dla wygody są udostępniane te złożone funkcje biblioteki matematycznej umożliwiające ograniczone manipulowanie liczbami złożonymi w kodzie użytkownika:

|Funkcja|Opis|
|-|-|
|[_Cmulcc, _FCmulcc, _LCmulcc](../c-runtime-library/reference/cmulcc-fcmulcc-lcmulcc.md)|Pomnóż dwie liczby zespolone|
|[_Cmulcr, _FCmulcr, _LCmulcr](../c-runtime-library/reference/cmulcr-fcmulcr-lcmulcr.md)|Mnożenie złożonej i liczby zmiennoprzecinkowej|

## <a name="see-also"></a>Zobacz także

[Procedury środowiska uruchomieniowego języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
