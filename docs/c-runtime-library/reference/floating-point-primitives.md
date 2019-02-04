---
title: Zmiennoprzecinkowe elementów podstawowych
ms.date: 01/31/2019
apiname:
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
apilocation:
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
apitype: DLLExport
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
ms.openlocfilehash: 230d0def145bcb443437b59303b2b36e348da2bb
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703382"
---
# <a name="floating-point-primitives"></a>Zmiennoprzecinkowe elementów podstawowych

Specyficzne dla firmy Microsoft pierwotnych funkcje, które są używane do implementowania niektóre standardowe środowisko uruchomieniowe funkcje biblioteki języka C (CRT) zmiennoprzecinkowych. Są one opisane tutaj, aby informacje były kompletne, ale nie są zalecane do użytku. Niektóre z tych funkcji są podane jako nieużywane, ponieważ są one znane problemów, dokładności, obsługa wyjątków i zgodność zachowanie IEEE 754. Istnieją one w bibliotece tylko w przypadku zgodności z poprzednimi wersjami. Do poprawnego zachowania przenośność i zgodność ze standardami, preferowanie standardowe funkcje liczb zmiennoprzecinkowych za pośrednictwem tych funkcji.

## <a name="dclass-ldclass-fdclass"></a>_dclass, _ldclass, _fdclass

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

Tych wartości zmiennoprzecinkowych pierwotnych zaimplementować wersji C — makro CRT [fpclassify —](fpclassify.md) dla typów zmiennopozycyjnych. Klasyfikacja argument *x* jest zwracany jako jeden z tych stałe zdefiniowane w math.h:

|Wartość|Opis|
|-----------|-----------------|
| **FP_NAN** | Cichy, sygnalizowanie lub nieokreślony NaN |
| **FP_INFINITE** | Nieskończoność dodatnia lub ujemna |
| **FP_NORMAL** | Dodatnie lub ujemne różna od zera wartość znormalizowaną |
| **FP_SUBNORMAL** | Dodatnia lub ujemna wartość (nieznormalizowany) subnormal |
| **FP_ZERO** | Dodatnią lub ujemną wartość zero |

Aby uzyskać dodatkowe szczegóły, możesz użyć specyficzne dla firmy Microsoft [_fpclass, _fpclassf](fpclass-fpclassf.md) funkcji. Użyj [fpclassify —](fpclassify.md) makro lub funkcja przenośności.

## <a name="dsign-ldsign-fdsign"></a>_dsign _ldsign, _fdsign

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

Implementowanie tych wartości zmiennoprzecinkowych pierwotnych [signbit —](signbit.md) makro lub funkcja w CRT. Zwraca wartość niezerową, jeśli ustawiono bit znaku w mantysę (mantysy) argument *x*i 0, jeśli nie ustawiono bitu znaku.

## <a name="dpcomp-ldpcomp-fdpcomp"></a>_dpcomp _ldpcomp, _fdpcomp

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

Tych wartości zmiennoprzecinkowych pierwotnych wykonać dwa argumenty *x* i *y*i zwracają wartość, która zawiera ich szeregowania relacji, wyrażone jako operatora testu koniunkcji lub te stałe zdefiniowane w math.h:

| Wartość | Opis |
|------------|-----------------|
| **_FP_LT** | *x* jest uznawana za mniej niż *y* |
| **_FP_EQ** | *x* jest uznawana za równe *y* |
| **_FP_GT** | *x* jest uznawana za większy niż *y* |

Implementowanie tych wartości pierwotnych [isgreater, isgreaterequal, isless, islessequal, islessgreater i isunordered](floating-point-ordering.md) makra i funkcje w CRT.

## <a name="dtest-ldtest-fdtest"></a>_dtest, _ldtest, _fdtest

### <a name="syntax"></a>Składnia

```C
short __cdecl _dtest(double* px);
short __cdecl _ldtest(long double* px);
short __cdecl _fdtest(float* px);
```

### <a name="parameters"></a>Parametry

*px*<br/>
Wskaźnik do argumentu zmiennoprzecinkowego.

### <a name="remarks"></a>Uwagi

Tych wartości zmiennoprzecinkowych pierwotnych implementacji C++ wersje funkcji CRT [fpclassify —](fpclassify.md) dla typów zmiennopozycyjnych. Argument *x* jest obliczane i klasyfikacji są zwracane jako jeden z tych stałe zdefiniowane w math.h:

|Wartość|Opis|
|-----------|-----------------|
| **FP_NAN** | Cichy, sygnalizowanie lub nieokreślony NaN |
| **FP_INFINITE** | Nieskończoność dodatnia lub ujemna |
| **FP_NORMAL** | Dodatnie lub ujemne różna od zera wartość znormalizowaną |
| **FP_SUBNORMAL** | Dodatnia lub ujemna wartość (nieznormalizowany) subnormal |
| **FP_ZERO** | Dodatnią lub ujemną wartość zero |

Aby uzyskać dodatkowe szczegóły, możesz użyć specyficzne dla firmy Microsoft [_fpclass, _fpclassf](fpclass-fpclassf.md) funkcji. Użyj [fpclassify —](fpclassify.md) funkcji przenośności.

## <a name="dint-ldint-fdint"></a>_d_int, _ld_int, _fd_int

### <a name="syntax"></a>Składnia

```C
short __cdecl _d_int(double* px, short exp);
short __cdecl _ld_int(long double* px, short exp);
short __cdecl _fd_int(float* px, short exp);
```

### <a name="parameters"></a>Parametry

*px*<br/>
Wskaźnik do argumentu zmiennoprzecinkowego.

*exp*<br/>
Wykładnik jako typ całkowitoliczbowy.

### <a name="remarks"></a>Uwagi

Tych wartości zmiennoprzecinkowych pierwotnych zająć wskaźnik do wartości zmiennoprzecinkowych *px* i wartość wykładnika *exp*i usuwają część ułamkową wartości zmiennoprzecinkowych pod danym wykładnik, jeśli jest to możliwe . Wartość zwracana jest wynikiem **fpclassify —** na wartość wejściowa w *px* przypadku NaN lub nieskończoności i wartości danych wyjściowych w *px* inaczej.

## <a name="dscale-ldscale-fdscale"></a>_dscale, _ldscale, _fdscale

### <a name="syntax"></a>Składnia

```C
short __cdecl _dscale(double* px, long exp);
short __cdecl _ldscale(long double* px, long exp);
short __cdecl _fdscale(float* px, long exp);
```

### <a name="parameters"></a>Parametry

*px*<br/>
Wskaźnik do argumentu zmiennoprzecinkowego.

*exp*<br/>
Wykładnik jako typ całkowitoliczbowy.

### <a name="remarks"></a>Uwagi

Tych wartości zmiennoprzecinkowych pierwotnych zająć wskaźnik do wartości zmiennoprzecinkowych *px* i wartość wykładnika *exp*, i skalowanie wartości w *px* przez 2<sup> *exp*</sup>, jeśli to możliwe. Wartość zwracana jest wynikiem **fpclassify —** na wartość wejściowa w *px* przypadku NaN lub nieskończoności i wartości danych wyjściowych w *px* inaczej. Do celów przenośności, Preferuj [ldexp —, ldexpf — i ldexpl](ldexp.md) funkcji.

## <a name="dunscale-ldunscale-fdunscale"></a>_dunscale, _ldunscale, _fdunscale

### <a name="syntax"></a>Składnia

```C
short __cdecl _dunscale(short* pexp, double* px);
short __cdecl _ldunscale(short* pexp, long double* px);
short __cdecl _fdunscale(short* pexp, float* px);
```

### <a name="parameters"></a>Parametry

*pexp*<br/>
Wskaźnik do wykładnik jako typ całkowitoliczbowy.

*px*<br/>
Wskaźnik do argumentu zmiennoprzecinkowego.

### <a name="remarks"></a>Uwagi

Tych wartości zmiennoprzecinkowych pierwotnych podzielić wartość zmiennoprzecinkową wskazywanej przez *px* mantysę (mantysy) i wykładnik, jeśli jest to możliwe. Mantysy jest skalowana w taki sposób, że wartość bezwzględna jest większa lub równa 0,5 i mniejszą niż 1,0. Wykładnik jest wartością *n*, gdzie oryginalna wartość zmiennoprzecinkowa jest równa skalowanych mantysę razy 2<sup>*n*</sup>. Wykładnik tej liczby całkowitej *n* jest przechowywany w lokalizacji wskazywanej przez *pexp*. Wartość zwracana jest wynikiem **fpclassify —** na wartość wejściowa w *px* Jeśli jest infinity lub NaN, a w przeciwnym razie wartość danych wyjściowych. Do celów przenośności, Preferuj [frexp —, frexpf —, frexpl —](frexp.md) funkcji.

## <a name="dexp-ldexp-fdexp"></a>_dexp, _ldexp, _fdexp

### <a name="syntax"></a>Składnia

```C
short __cdecl _dexp(double* px, double y, long exp);
short __cdecl _ldexp(long double* px, long double y, long exp);
short __cdecl _fdexp(float* px, float y, long exp);
```

### <a name="parameters"></a>Parametry

*y*<br/>
Argument funkcji zmiennoprzecinkowej.

*px*<br/>
Wskaźnik do argumentu zmiennoprzecinkowego.

*exp*<br/>
Wykładnik jako typ całkowitoliczbowy.

### <a name="remarks"></a>Uwagi

Tych wartości zmiennoprzecinkowych pierwotnych konstruowania wartość zmiennoprzecinkowa w lokalizacji wskazywanej przez *px* równa *y* * 2<sup>*exp*</sup>. Wartość zwracana jest wynikiem **fpclassify —** na wartość wejściowa w *y* przypadku NaN lub nieskończoności i wartości danych wyjściowych w *px* inaczej. Do celów przenośności, Preferuj [ldexp —, ldexpf — i ldexpl](ldexp.md) funkcji.

## <a name="dnorm-fdnorm"></a>_dnorm, _fdnorm

### <a name="syntax"></a>Składnia

```C
short __cdecl _dnorm(unsigned short* ps);
short __cdecl _fdnorm(unsigned short* ps);
```

### <a name="parameters"></a>Parametry

*PS*<br/>
Wskaźnik na logiczną reprezentację w postaci wartość zmiennoprzecinkowa, wyrażone jako tablicę **niepodpisane** **krótki**.

### <a name="remarks"></a>Uwagi

Tych wartości zmiennoprzecinkowych pierwotnych normalizacji część ułamkową underflowed wartości zmiennoprzecinkowe i dostosować *cechy*, lub obciążonej wykładnik, do dopasowania. Wartość jest przekazywana jako bitowa reprezentacja typu zmiennoprzecinkowego konwertowany na tablicę **niepodpisane** **krótki** za pośrednictwem `_double_val`, `_ldouble_val`, lub `_float_val` typu Unia punning zadeklarowanych w math.h. Wartość zwracana jest wynikiem **fpclassify —** na wejściowych wartość zmiennoprzecinkowa, jeśli jest infinity lub NaN, a w przeciwnym razie wartość danych wyjściowych.

## <a name="dpoly-ldpoly-fdpoly"></a>_dpoly, _ldpoly, _fdpoly

### <a name="syntax"></a>Składnia

```C
double __cdecl _dpoly(double x, double const* table, int n);
long double __cdecl _ldpoly(long double x, long double const* table, int n);
float __cdecl _fdpoly(float x, _float const* table, int n);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Argument funkcji zmiennoprzecinkowej.

*Tabela*<br/>
Wskaźnik do tabeli stałej współczynników wielomianu.

*n*<br/>
Kolejność wielomianu do oceny.

### <a name="remarks"></a>Uwagi

Tych wartości zmiennoprzecinkowych pierwotnych zwracają oceny *x* w wielomianu kolejności *n* którego współczynniki są reprezentowane przez odpowiednie wartości stałej w *tabeli*. Na przykład, jeśli *tabeli*\[0] = 3.0, *tabeli*\[1] = 4.0, *tabeli*\[2] = 5.0 i *n* = 2, czyli przedstawia liczbę wielomianowej x 5.0<sup>2</sup> + 4.0 x + 3.0. Jeśli ta wielomianu sprawdzania pod kątem *x* 2.0, wynik jest 31.0. Te funkcje nie są używane wewnętrznie.

## <a name="dlog-dlog-dlog"></a>_dlog _dlog, _dlog

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
Znacznik, który steruje podstawy, aby korzystać z, 0 dla podstawowego *e* i większe niż zero na podstawie 10.

### <a name="remarks"></a>Uwagi

Tych wartości zmiennoprzecinkowych pierwotnych zwracają logarytmu naturalnego *x*, ln (*x*) lub dziennik<sub>*e*</sub>(*x*), gdy *base_flag* wynosi 0. Zwracają dziennika podstawowego 10 *x*, lub dziennika<sub>10</sub>(*x*), gdy *base_flag* jest różna od zera. Te funkcje nie są używane wewnętrznie. Do celów przenośności, Preferuj funkcji [dziennika, logf —, logl log10, log10f — i log10l](log-logf-log10-log10f.md).

## <a name="dsin-ldsin-fdsin"></a>_dsin, _ldsin, _fdsin

### <a name="syntax"></a>Składnia

```C
double __cdecl _dsin(double x, unsigned int quadrant);
long double __cdecl _ldsin(long double x, unsigned int quadrant);
float __cdecl _fdsin(float x, unsigned int quadrant);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Argument funkcji zmiennoprzecinkowej.

*quadrant*<br/>
Przesunięcie Quadrant 0, 1, 2 lub 3, aby użyć, aby wygenerować `sin`, `cos`, `-sin`, i `-cos` wyników.

### <a name="remarks"></a>Uwagi

Tych wartości zmiennoprzecinkowych pierwotnych zwracają sinusa *x* przesunięcia przez *quadrant* modulo 4. Skutecznie, zwracają sinusa, cosinusa, - sinusa i - cosinus *x* podczas *quadrant* modulo 4 jest odpowiednio na 0, 1, 2 lub 3,. Te funkcje nie są używane wewnętrznie. Do celów przenośności, Preferuj [sin, sinf — sinl —](sin-sinf-sinl.md), [cos, cosf — i cosl —](cos-cosf-cosl.md) funkcji.

## <a name="requirements"></a>Wymagania

Header: \<math.h>

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf —](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal —](isnormal.md)<br/>
[COS cosf —, cosl —](cos-cosf-cosl.md)<br/>
[frexp —, frexpf —, frexpl —](frexp.md)<br/>
[ldexp — ldexpf — i ldexpl](ldexp.md)<br/>
[Dziennik, logf —, logl, log10 log10f —, log10l](log-logf-log10-log10f.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
