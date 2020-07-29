---
title: Zmiennoprzecinkowe typy pierwotne
ms.date: 4/2/2020
api_name:
- _dclass
- _ldclass
- _fdclass
- _dsign
- _ldsign
- _fdsign
- _dpcomp
- _ldpcomp
- _fdpcomp
- _dtest
- _ldtest
- _fdtest
- _d_int
- _ld_int
- _fd_int
- _dscale
- _ldscale
- _fdscale
- _dunscale
- _ldunscale
- _fdunscale
- _dexp
- _ldexp
- _fdexp
- _dnorm
- _fdnorm
- _dpoly
- _ldpoly
- _fdpoly
- _dlog
- _ldlog
- _fdlog
- _dsin
- _ldsin
- _fdsin
- _o__d_int
- _o__dclass
- _o__dlog
- _o__dnorm
- _o__dpcomp
- _o__dpoly
- _o__dscale
- _o__dsign
- _o__dsin
- _o__dtest
- _o__dunscale
- _o__fd_int
- _o__fdclass
- _o__fdexp
- _o__fdlog
- _o__fdpcomp
- _o__fdpoly
- _o__fdscale
- _o__fdsign
- _o__fdsin
- _o__ld_int
- _o__ldclass
- _o__ldexp
- _o__ldlog
- _o__ldpcomp
- _o__ldpoly
- _o__ldscale
- _o__ldsign
- _o__ldsin
- _o__ldtest
- _o__ldunscale
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _dclass
- _ldclass
- _fdclass
- _dsign
- _ldsign
- _fdsign
- _dpcomp
- _ldpcomp
- _fdpcomp
- _dtest
- _ldtest
- _fdtest
- _d_int
- _ld_int
- _fd_int
- _dscale
- _ldscale
- _fdscale
- _dunscale
- _ldunscale
- _fdunscale
- _dexp
- _ldexp
- _fdexp
- _dnorm
- _fdnorm
- _dpoly
- _ldpoly
- _fdpoly
- _dlog
- _ldlog
- _fdlog
- _dsin
- _ldsin
- _fdsin
helpviewer_keywords:
- _dclass
- _ldclass
- _fdclass
- _dsign
- _ldsign
- _fdsign
- _dpcomp
- _ldpcomp
- _fdpcomp
- _dtest
- _ldtest
- _fdtest
- _d_int
- _ld_int
- _fd_int
- _dscale
- _ldscale
- _fdscale
- _dunscale
- _ldunscale
- _fdunscale
- _dexp
- _ldexp
- _fdexp
- _dnorm
- _fdnorm
- _dpoly
- _ldpoly
- _fdpoly
- _dlog
- _ldlog
- _fdlog
- _dsin
- _ldsin
- _fdsin
ms.openlocfilehash: e28c873206d8f050dbde2afc9ebfe3540b6642ff
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218689"
---
# <a name="floating-point-primitives"></a>Zmiennoprzecinkowe typy pierwotne

Specyficzne dla firmy Microsoft funkcje pierwotne, które są używane do implementowania niektórych funkcji zmiennoprzecinkowych standardowej biblioteki środowiska uruchomieniowego języka C (CRT). Są one udokumentowane w tym miejscu pod kątem kompletności, ale nie są zalecane do użycia. Niektóre z tych funkcji są uważane za nieużywane, ponieważ wiadomo, że występują problemy z dokładnością, obsługą wyjątków i zgodnością z zachowaniem IEEE-754. Istnieją one w bibliotece tylko w celu zapewnienia zgodności z poprzednimi wersjami. Aby poprawić zachowanie, przenośność i zgodność ze standardami, Preferuj standardowe funkcje zmiennoprzecinkowe za pośrednictwem tych funkcji.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="_dclass-_ldclass-_fdclass"></a>_dclass, _ldclass, _fdclass

### <a name="syntax"></a>Składnia

```C
short __cdecl _dclass(double x);
short __cdecl _ldclass(long double x);
short __cdecl _fdclass(float x);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Argument funkcji zmiennoprzecinkowej.

### <a name="remarks"></a>Uwagi

Te elementy podstawowe zmiennoprzecinkowe implementują wersje języka C [fpclassify —](fpclassify.md) makro CRT dla typów zmiennoprzecinkowych. Klasyfikacja argumentu *x* jest zwracana jako jedna ze stałych, zdefiniowana w Math. h:

|Wartość|Opis|
|-----------|-----------------|
| **FP_NAN** | Cichy, sygnalizujący lub nieokreślony NaN |
| **FP_INFINITE** | Dodatnia lub ujemna nieskończoność |
| **FP_NORMAL** | Dodatnia lub negatywna znormalizowana wartość różna od zera |
| **FP_SUBNORMAL** | Wartość dodatnia lub ujemna (nieznormalizowana) |
| **FP_ZERO** | Dodatnia lub ujemna wartość zerowa |

Aby uzyskać dodatkowe informacje, można użyć [_fpclass, _fpclassf](fpclass-fpclassf.md) funkcji. Użyj makra lub funkcji [fpclassify —](fpclassify.md) do przenoszenia.

## <a name="_dsign-_ldsign-_fdsign"></a>_dsign, _ldsign, _fdsign

### <a name="syntax"></a>Składnia

```C
int __cdecl _dsign(double x);
int __cdecl _ldsign(long double x);
int __cdecl _fdsign(float x);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Argument funkcji zmiennoprzecinkowej.

### <a name="remarks"></a>Uwagi

Te elementy podstawowe zmiennoprzecinkowe implementują makro [signbit —](signbit.md) lub funkcję w CRT. Zwracają one wartość różną od zera, jeśli bit znaku jest ustawiony w mantysę (mantysy) argumentu *x*, i 0, jeśli bit znaku nie jest ustawiony.

## <a name="_dpcomp-_ldpcomp-_fdpcomp"></a>_dpcomp, _ldpcomp, _fdpcomp

### <a name="syntax"></a>Składnia

```C
int __cdecl _dpcomp(double x, double y);
int __cdecl _ldpcomp(long double x, long double y);
int __cdecl _fdpcomp(float x, float y);
```

### <a name="parameters"></a>Parametry

*x*, *y*<br/>
Argumenty funkcji zmiennoprzecinkowej.

### <a name="remarks"></a>Uwagi

Te elementy podstawowe zmiennoprzecinkowe przyjmują dwa argumenty, *x* i *y*, i zwracają wartość pokazującą relację kolejności, wyrażoną jako bitowe lub te stałe, zdefiniowane w Math. h:

| Wartość | Opis |
|------------|-----------------|
| **_FP_LT** | *x* może być traktowany jako mniejszy niż *y* |
| **_FP_EQ** | wartość *x* może być uważana za równą *y* |
| **_FP_GT** | *x* może być traktowany jako większy niż *y* |

Te elementy pierwotne implementują makra isisgreaterequal, [islessequal, islessgreater i isunordered](floating-point-ordering.md) oraz funkcje w CRT.

## <a name="_dtest-_ldtest-_fdtest"></a>_dtest, _ldtest, _fdtest

### <a name="syntax"></a>Składnia

```C
short __cdecl _dtest(double* px);
short __cdecl _ldtest(long double* px);
short __cdecl _fdtest(float* px);
```

### <a name="parameters"></a>Parametry

*piks.*<br/>
Wskaźnik do argumentu zmiennoprzecinkowego.

### <a name="remarks"></a>Uwagi

Te elementy podstawowe zmiennoprzecinkowe implementują wersje C++ funkcji CRT [fpclassify —](fpclassify.md) dla typów zmiennoprzecinkowych. Argument *x* jest obliczany, a klasyfikacja jest zwracana jako jedna ze stałych, zdefiniowana w Math. h:

|Wartość|Opis|
|-----------|-----------------|
| **FP_NAN** | Cichy, sygnalizujący lub nieokreślony NaN |
| **FP_INFINITE** | Dodatnia lub ujemna nieskończoność |
| **FP_NORMAL** | Dodatnia lub negatywna znormalizowana wartość różna od zera |
| **FP_SUBNORMAL** | Wartość dodatnia lub ujemna (nieznormalizowana) |
| **FP_ZERO** | Dodatnia lub ujemna wartość zerowa |

Aby uzyskać dodatkowe informacje, można użyć [_fpclass, _fpclassf](fpclass-fpclassf.md) funkcji. Użyj funkcji [fpclassify —](fpclassify.md) , aby przenieść.

## <a name="_d_int-_ld_int-_fd_int"></a>_d_int, _ld_int, _fd_int

### <a name="syntax"></a>Składnia

```C
short __cdecl _d_int(double* px, short exp);
short __cdecl _ld_int(long double* px, short exp);
short __cdecl _fd_int(float* px, short exp);
```

### <a name="parameters"></a>Parametry

*piks.*<br/>
Wskaźnik do argumentu zmiennoprzecinkowego.

*EXP*<br/>
Wykładnik jako typ całkowity.

### <a name="remarks"></a>Uwagi

Te elementy podstawowe zmiennoprzecinkowe przyjmują wskaźnik do wartości zmiennoprzecinkowej *px* i wartości wykładnika, a następnie usuwają część ułamkową wartości zmiennoprzecinkowej poniżej danego wykładniku *, jeśli*jest to możliwe. Zwracana wartość jest wynikiem **fpclassify —** wartości wejściowej w *pikselach* , jeśli jest to NaN lub nieskończoność, a wartość wyjściowa (w *pikselach* ) w przeciwnym razie.

## <a name="_dscale-_ldscale-_fdscale"></a>_dscale, _ldscale, _fdscale

### <a name="syntax"></a>Składnia

```C
short __cdecl _dscale(double* px, long exp);
short __cdecl _ldscale(long double* px, long exp);
short __cdecl _fdscale(float* px, long exp);
```

### <a name="parameters"></a>Parametry

*piks.*<br/>
Wskaźnik do argumentu zmiennoprzecinkowego.

*EXP*<br/>
Wykładnik jako typ całkowity.

### <a name="remarks"></a>Uwagi

Te elementy podstawowe zmiennoprzecinkowe przyjmują wskaźnik do wartości zmiennoprzecinkowej *px* i wartości wykładnika, a następnie *skalują wartość w* *px* <sup>*o 2,*</sup>Jeśli to możliwe. Zwracana wartość jest wynikiem **fpclassify —** wartości wejściowej w *pikselach* , jeśli jest to NaN lub nieskończoność, a wartość wyjściowa (w *pikselach* ) w przeciwnym razie. W przypadku przenośności Preferuj funkcje [ldexp —, ldexpf — i ldexpl](ldexp.md) .

## <a name="_dunscale-_ldunscale-_fdunscale"></a>_dunscale, _ldunscale, _fdunscale

### <a name="syntax"></a>Składnia

```C
short __cdecl _dunscale(short* pexp, double* px);
short __cdecl _ldunscale(short* pexp, long double* px);
short __cdecl _fdunscale(short* pexp, float* px);
```

### <a name="parameters"></a>Parametry

*pexp*<br/>
Wskaźnik do wykładnika jako typ całkowity.

*piks.*<br/>
Wskaźnik do argumentu zmiennoprzecinkowego.

### <a name="remarks"></a>Uwagi

Te elementy podstawowe zmiennoprzecinkowe łamią wartość zmiennoprzecinkową, która została przestawiona *na mantysę* (mantysy) i wykładnik, jeśli jest to możliwe. Mantysę jest skalowany w taki sposób, że wartość bezwzględna jest większa lub równa 0,5 i mniejsza niż 1,0. Wykładnik jest wartością *n*, gdzie oryginalna wartość zmiennoprzecinkowa jest równa skalowanej mantysę razy 2<sup>*n*</sup>. Ten wykładnik liczby całkowitej *n* jest przechowywany w lokalizacji wskazywanej przez *pexp*. Zwracana wartość jest wynikiem **fpclassify —** wartości wejściowej w *pikselach* , jeśli jest to NaN lub nieskończoność, a na wartość wyjściową w przeciwnym razie. W przypadku przenośności Preferuj funkcje [frexp —, frexpf —, frexpl](frexp.md) .

## <a name="_dexp-_ldexp-_fdexp"></a>_dexp, _ldexp, _fdexp

### <a name="syntax"></a>Składnia

```C
short __cdecl _dexp(double* px, double y, long exp);
short __cdecl _ldexp(long double* px, long double y, long exp);
short __cdecl _fdexp(float* px, float y, long exp);
```

### <a name="parameters"></a>Parametry

*t*<br/>
Argument funkcji zmiennoprzecinkowej.

*piks.*<br/>
Wskaźnik do argumentu zmiennoprzecinkowego.

*EXP*<br/>
Wykładnik jako typ całkowity.

### <a name="remarks"></a>Uwagi

Te elementy pierwotne zmiennoprzecinkowe konstruują wartość zmiennoprzecinkową w lokalizacji wskazywanej przez *px pikseli* równej *y* <sup>** 2.*</sup> Zwracana wartość jest wynikiem **fpclassify —** wartości wejściowej ( *y* ), jeśli jest to NaN lub nieskończoność, a wartość wyjściowa (w *pikselach* ) w przeciwnym razie. W przypadku przenośności Preferuj funkcje [ldexp —, ldexpf — i ldexpl](ldexp.md) .

## <a name="_dnorm-_fdnorm"></a>_dnorm, _fdnorm

### <a name="syntax"></a>Składnia

```C
short __cdecl _dnorm(unsigned short* ps);
short __cdecl _fdnorm(unsigned short* ps);
```

### <a name="parameters"></a>Parametry

*iloczyn*<br/>
Wskaźnik na bitową reprezentację wartości zmiennoprzecinkowej wyrażonej jako tablica **`unsigned short`** .

### <a name="remarks"></a>Uwagi

Te elementy podstawowe zmiennoprzecinkowe normalizią część ułamkową bezosiowej wartości zmiennoprzecinkowej i dostosowują *charakterystykę*lub wykładnikę, aby dopasować. Wartość jest przenoszona jako bitowa reprezentacja typu zmiennoprzecinkowego konwertowana na tablicę **`unsigned short`** przez `_double_val` , `_ldouble_val` lub `_float_val` typu punning Union zadeklarowanej w Math. h. Wartość zwracana jest wynikiem **fpclassify —** wartości wejściowej zmiennoprzecinkowej, jeśli jest to NaN lub nieskończoność, a wartość wyjściowa w przeciwnym razie.

## <a name="_dpoly-_ldpoly-_fdpoly"></a>_dpoly, _ldpoly, _fdpoly

### <a name="syntax"></a>Składnia

```C
double __cdecl _dpoly(double x, double const* table, int n);
long double __cdecl _ldpoly(long double x, long double const* table, int n);
float __cdecl _fdpoly(float x, _float const* table, int n);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Argument funkcji zmiennoprzecinkowej.

*tabele*<br/>
Wskaźnik do tabeli stałych współczynników dla wielomianu.

*Azotan*<br/>
Kolejność wielomianu do obliczenia.

### <a name="remarks"></a>Uwagi

Te elementy pierwotne zmiennoprzecinkowe zwracają ocenę *x* w wielomianie kolejności *n* , której współczynniki są reprezentowane przez odpowiadające im wartości stałe w *tabeli*. Na przykład jeśli *tabela* \[ 0] = 3,0, *tabela* \[ 1] = 4,0, *tabela* \[ 2] = 5,0 i *n* = 2, reprezentuje wielomian 5.0 x<sup>2</sup> + 4.0 x + 3,0. W przypadku obliczenia tego wielomianu dla *x* z 2,0, wynik wynosi 31,0. Te funkcje nie są używane wewnętrznie.

## <a name="_dlog-_dlog-_dlog"></a>_dlog, _dlog, _dlog

### <a name="syntax"></a>Składnia

```C
double __cdecl _dlog(double x, int base_flag);
long double __cdecl _ldlog(long double x, int base_flag);
float __cdecl _fdlog(float x, int base_flag);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Argument funkcji zmiennoprzecinkowej.

*base_flag*<br/>
Flaga, która kontroluje podstawę do użycia, 0 dla podstawy *e* i zero dla podstawowego 10.

### <a name="remarks"></a>Uwagi

Te elementy pierwotne zmiennoprzecinkowe zwracają naturalny dziennik *x*, ln (*x*) lub log<sub>*e*</sub>(*x*), gdy *base_flag* wynosi 0. Zwracają one bazę dzienników 10 *x*lub<sub>10</sub>(*x*), gdy *base_flag* jest różna od zera. Te funkcje nie są używane wewnętrznie. W przypadku przenośności wolisz rejestrować usługi Functions [, logf —, logl, log10 —, log10f — i log10l](log-logf-log10-log10f.md).

## <a name="_dsin-_ldsin-_fdsin"></a>_dsin, _ldsin, _fdsin

### <a name="syntax"></a>Składnia

```C
double __cdecl _dsin(double x, unsigned int quadrant);
long double __cdecl _ldsin(long double x, unsigned int quadrant);
float __cdecl _fdsin(float x, unsigned int quadrant);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Argument funkcji zmiennoprzecinkowej.

*ćwiartk*<br/>
Przesunięcie ćwiartki 0, 1, 2 lub 3, które ma być używane do tworzenia `sin` , `cos` , `-sin` i `-cos` wyników.

### <a name="remarks"></a>Uwagi

Te elementy pierwotne zmiennoprzecinkowe zwracają sinus przesunięcia *x* do *ćwiartki* modulo 4. Efektywnie zwraca sinus, cosinus,-sinus i-cosinus *x* , gdy *Ćwiartka* modulo 4 jest odpowiednio 0, 1, 2 lub 3. Te funkcje nie są używane wewnętrznie. W przypadku przenośności Preferuj funkcje [Sin, SINF —, sinl](sin-sinf-sinl.md), [cos, cosf — i COSL](cos-cosf-cosl.md) .

## <a name="requirements"></a>Wymagania

Nagłówki\<math.h>

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
[cos, cosf, cosl](cos-cosf-cosl.md)<br/>
[frexp —, frexpf —, frexpl](frexp.md)<br/>
[ldexp —, ldexpf — i ldexpl](ldexp.md)<br/>
[log, logf —, logl, log10 —, log10f —, log10l](log-logf-log10-log10f.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
