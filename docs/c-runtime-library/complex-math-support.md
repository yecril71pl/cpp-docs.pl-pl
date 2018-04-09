---
title: Obsługa złożonych matematyczne C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/30/2018
ms.technology:
- cpp-standard-libraries
ms.topic: article
f1_keywords:
- c.complex
dev_langs:
- C++
helpviewer_keywords:
- complex numbers, math routines
- math routines
- complex numbers
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3533d43783648c43b657c8073ada0c2042808b10
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2018
---
# <a name="c-complex-math-support"></a>Obsługa złożonych matematyczne C

Biblioteka Microsoft C Runtime (CRT) zapewnia funkcje biblioteki matematyczne złożonych, wraz ze wszystkimi wymaganymi przez ISO C99. Kompilator nie obsługuje bezpośrednio **złożonych** lub **_Complex** — słowo kluczowe, w związku z tym przez firmę Microsoft implementacją używa struktury typów, aby reprezentować liczby złożone.

Te funkcje są wdrażane do zrównoważenia wydajności z poprawności. Ponieważ produkujących poprawnie zaokrąglony wynik może być zbyt duży, te funkcje są przeznaczone do wydajnie tworzyć Zamknij zbliżenia się poprawnie zaokrąglony wynik. W większości przypadków wyniku zwracany znajduje się w +/-1 ulp poprawnie zaokrąglony wyniku, chociaż może się zdarzyć, gdy istnieje większej dokładności.

Procedury matematyczne złożonych polegać na wartość zmiennoprzecinkowa punktu funkcje biblioteki matematyczne ich wdrażania. Te funkcje mają różne implementacje dla innej architektury Procesora. Na przykład x86 32-bitowych CRT może mieć inną implementację niż x64 64-bitowych CRT. Ponadto niektóre funkcje mogą mieć wiele implementacji dla danej architektury Procesora. Najbardziej efektywne implementacji wybrano dynamicznie w czasie wykonywania w zależności od zbiór instrukcji obsługiwane przez procesor CPU. Na przykład w 32-bitowych x86 CRT, niektóre funkcje mają zarówno x87 implementacji i implementację SSE2. Podczas uruchamiania na procesora CPU obsługującego usługę SSE2, szybsze implementacji SSE2 jest używany. Podczas uruchamiania na Procesorze, który nie obsługuje SSE2, wolniejsze x87 implementacji jest używana. Ponieważ różnych implementacji funkcji biblioteki matematyczne mogą używać różnych instrukcji procesora CPU i różnych algorytmów w celu uzyskania ich wyników, funkcje może wygenerować różne wyniki we wszystkich procesorach. W większości przypadków wyniki są w +/-1 ulp poprawnie zaokrąglony wyniku, ale na rzeczywistą wydajność może się różnić we wszystkich procesorach.

## <a name="types-used-in-complex-math"></a>Typy używane w złożonych matematyczne

Przez firmę Microsoft implementacją nagłówka complex.h definiuje te typy jako odpowiedniki dla C99 standardowe natywnych złożonych typów:

|Standardowe|Typ firmy Microsoft|
|-|-|
|**złożone float** lub **float _Complex**|**_FComplex**|
|**podwójne złożone** lub **_Complex podwójne**|**_DComplex**|
|**Long double złożone** lub **_Complex podwójnej długości**|**_LComplex**|

Nagłówek math.h definiuje typu oddzielnych **_complex struktury**używane do [_cabs —](../c-runtime-library/reference/cabs.md) funkcji. **_Complex struktury** typu nie jest używany przez funkcje równoważne matematyczne złożonych [pliki cab, cabsf, cabsl —](../c-runtime-library/reference/cabs-cabsf-cabsl.md).

## <a name="complex-constants-and-macros"></a>Stałe złożone i makra

**I** jest zdefiniowany jako **float** typu złożonego **_FComplex** zainicjowane przez `{ 0.0f, 1.0f }`.

## <a name="trigonometric-functions"></a>Funkcje trygonometryczne

|Funkcja|Opis|
|-|-|
|[cacos, cacosf, cacosl](../c-runtime-library/reference/cacos-cacosf-cacosl.md)|Obliczenia bazy danych złożonych arcus cosinus liczby złożone|
|[casin, casinf, casinl](../c-runtime-library/reference/casin-casinf-casinl.md)|Obliczenia bazy danych złożonych arcus sinus liczby złożone|
|[catan, catanf, catanl](../c-runtime-library/reference/catan-catanf-catanl.md)|Obliczenia bazy danych złożonych arcus tangens liczby złożone|
|[ccos, ccosf, ccosl](../c-runtime-library/reference/ccos-ccosf-ccosl.md)|Obliczenia bazy danych złożonych cosinus liczby złożone|
|[csin, csinf, csinl](../c-runtime-library/reference/csin-csinf-csinl.md)|Obliczenia bazy danych złożonych sinus liczby złożone|
|[ctan, ctanf, ctanl](../c-runtime-library/reference/ctan-ctanf-ctanl.md)|Obliczenia bazy danych złożonych tangens liczby złożone|

## <a name="hyperbolic-functions"></a>Funkcje hiperboliczne

|Funkcja|Opis|
|-|-|
|[cacosh, cacoshf, cacoshl](../c-runtime-library/reference/cacosh-cacoshf-cacoshl.md)|Obliczenia bazy danych złożonych arcus cosinus hiperboliczny liczby złożone|
|[casinh, casinhf, casinhl](../c-runtime-library/reference/casinh-casinhf-casinhl.md)|Obliczenia bazy danych złożonych arcus sinus hiperboliczny liczby złożone|
|[catanh, catanhf, catanhl](../c-runtime-library/reference/catanh-catanhf-catanhl.md)|Obliczenia bazy danych złożonych arcus tangens hiperboliczny liczby złożone|
|[ccosh, ccoshf, ccoshl](../c-runtime-library/reference/ccosh-ccoshf-ccoshl.md)|Obliczenia bazy danych złożonych cosinus hiperboliczny liczby złożone|
|[csinh, csinhf, csinhl](../c-runtime-library/reference/csinh-csinhf-csinhl.md)|Obliczenia bazy danych złożonych sinus hiperboliczny liczby złożone|
|[ctanh, ctanhf, ctanhl](../c-runtime-library/reference/ctanh-ctanhf-ctanhl.md)|Obliczenia bazy danych złożonych tangens hiperboliczny liczby złożone|

## <a name="exponential-and-logarithmic-functions"></a>Funkcji wykładniczej i logarytmicznej

|Funkcja|Opis|
|-|-|
|[cexp, cexpf, cexpl](../c-runtime-library/reference/cexp-cexpf-cexpl.md)|Obliczeniowe złożone podstawowej -*e* wykładnicza liczby złożone|
|[clog, clogf, clogl](../c-runtime-library/reference/clog-clogf-clogl.md)|Obliczeniowe złożonych naturalny (podstawowy -*e*) logarytmu liczby złożone|
|[clog10, clog10f, clog10l](../c-runtime-library/reference/clog10-clog10f-clog10l.md)|Obliczenia bazy danych złożonych logarytm base 10 liczby złożone|

## <a name="power-and-absolute-value-functions"></a>Zasilania i wartość bezwzględna funkcji

|Funkcja|Opis|
|-|-|
|[cabs, cabsf, cabsl](../c-runtime-library/reference/cabs-cabsf-cabsl.md)|Złożona wartość bezwzględna (nazywane również normy, moduł lub wielkości) liczbą obliczeniowe|
|[cpow, cpowf, cpowl](../c-runtime-library/reference/cpow-cpowf-cpowl.md)|Obliczanie funkcji power złożonych x<sup>y</sup>|
|[csqrt, csqrtf, csqrtl](../c-runtime-library/reference/csqrt-csqrtf-csqrtl.md)|Obliczenia bazy danych złożonych pierwiastek kwadratowy liczby złożone|

## <a name="manipulation-functions"></a>Funkcje manipulowania

|Funkcja|Opis|
|-|-|
|[_Cbuild, _FCbuild, _LCbuild](../c-runtime-library/reference/cbuild-fcbuild-lcbuild.md)|Konstrukcja liczbą z rzeczywistą i urojony części|
|[carg, cargf, cargl](../c-runtime-library/reference/carg-cargf-cargl.md)|Obliczenia bazy danych argumentu liczbą (nazywanych również kąt fazy)|
|[cimag, cimagf, cimagl](../c-runtime-library/reference/cimag-cimagf-cimagl.md)|Obliczenia bazy danych urojony część liczby złożone|
|[conj, conjf, conjl](../c-runtime-library/reference/conj-conjf-conjl.md)|Obliczenia bazy danych zespolonej liczby złożone|
|[cproj, cprojf, cprojl](../c-runtime-library/reference/cproj-cprojf-cprojl.md)|Obliczenia bazy danych projekcji na kuli Riemanna liczby złożone|
|[creal, crealf, creall](../c-runtime-library/reference/creal-crealf-creall.md)|Obliczenia bazy danych rzeczywistych część liczby złożone|
|[normy normf, norml](../c-runtime-library/reference/norm-normf-norml1.md)|Obliczenia bazy danych kwadratów wielkość liczbą|

## <a name="operation-functions"></a>Funkcje operacji

Ponieważ liczby złożone nie są typu macierzystego kompilatora firmy Microsoft, standardowe operatory arytmetyczne nie są zdefiniowane na typy złożone. Dla wygody te funkcje biblioteki matematyczne złożonych umożliwiające manipulowania ograniczonej liczby złożone w kodzie użytkownika:

|Funkcja|Opis|
|-|-|
|[_Cmulcc, _FCmulcc, _LCmulcc](../c-runtime-library/reference/cmulcc-fcmulcc-lcmulcc.md)|Mnożenie dwie liczb złożone|
|[_Cmulcr, _FCmulcr, _LCmulcr](../c-runtime-library/reference/cmulcr-fcmulcr-lcmulcr.md)|Należy pomnożyć złożony i liczba zmiennoprzecinkowa|

## <a name="see-also"></a>Zobacz także

[Procedury czasu wykonywania według kategorii](../c-runtime-library/run-time-routines-by-category.md)