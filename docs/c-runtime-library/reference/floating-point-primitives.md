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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: d861fbf2b71d557354a60f65b8a76dc24ca1dd13
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346711"
---
# <a name="floating-point-primitives"></a>Zmiennoprzecinkowe typy pierwotne

Specyficzne dla firmy Microsoft funkcje pierwotne, które są używane do implementacji niektórych standardowych funkcji zmiennoprzecinkowych biblioteki wykonawczej C (CRT). Są one udokumentowane tutaj dla kompletności, ale nie są zalecane do użycia. Niektóre z tych funkcji są znane jako nieużywane, ponieważ wiadomo, że mają problemy z precyzją, obsługą wyjątków i zgodnością z zachowaniem IEEE-754. Istnieją one w bibliotece tylko dla zgodności z powrotem. W celu prawidłowego zachowania, przenośności i przestrzegania standardów preferuj standardowe funkcje zmiennoprzecinające nad tymi funkcjami.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="_dclass-_ldclass-_fdclass"></a>_dclass, _ldclass, _fdclass

### <a name="syntax"></a>Składnia

```C
short __cdecl _dclass(double x);
short __cdecl _ldclass(long double x);
short __cdecl _fdclass(float x);
```

### <a name="parameters"></a>Parametry

*X*<br/>
Argument funkcji zmiennoprzecinowej.

### <a name="remarks"></a>Uwagi

Te prymitywy zmiennoprzecinowe implementują wersje C makra [CRT fpclassify](fpclassify.md) dla typów zmiennoprzecinkowych. Klasyfikacja argumentu *x* jest zwracana jako jedna z tych stałych, zdefiniowana w math.h:

|Wartość|Opis|
|-----------|-----------------|
| **FP_NAN** | Cichy, sygnalizujący lub nieokreślony NaN |
| **FP_INFINITE** | Dodatnia lub ujemna nieskończoność |
| **FP_NORMAL** | Dodatnia lub ujemna znormalizowana wartość niezerowa |
| **FP_SUBNORMAL** | Dodatnia lub ujemna wartość subnormal (zdenormalowana) |
| **FP_ZERO** | Dodatnia lub ujemna wartość zerowa |

Aby uzyskać dodatkowe informacje, można użyć [funkcji _fpclass, _fpclassf](fpclass-fpclassf.md) specyficznych dla firmy Microsoft. Użyj [makra lub funkcji fpclassify, aby](fpclassify.md) uzyskać przenośność.

## <a name="_dsign-_ldsign-_fdsign"></a>_dsign, _ldsign, _fdsign

### <a name="syntax"></a>Składnia

```C
int __cdecl _dsign(double x);
int __cdecl _ldsign(long double x);
int __cdecl _fdsign(float x);
```

### <a name="parameters"></a>Parametry

*X*<br/>
Argument funkcji zmiennoprzecinowej.

### <a name="remarks"></a>Uwagi

Te prymitywy zmiennoprzecinowe implementują makro lub funkcję [signbit](signbit.md) w CRT. Zwracają wartość różną od zera, jeśli bit znaku jest ustawiony w significand (mantissa) *argumentu x*i 0, jeśli bit znaku nie jest ustawiony.

## <a name="_dpcomp-_ldpcomp-_fdpcomp"></a>_dpcomp, _ldpcomp, _fdpcomp

### <a name="syntax"></a>Składnia

```C
int __cdecl _dpcomp(double x, double y);
int __cdecl _ldpcomp(long double x, long double y);
int __cdecl _fdpcomp(float x, float y);
```

### <a name="parameters"></a>Parametry

*x*, *y*<br/>
Argumenty funkcji zmiennoprzecinowej.

### <a name="remarks"></a>Uwagi

Te prymitywy zmiennoprzecinowe przyjmują dwa argumenty, *x* i *y*i zwracają wartość, która pokazuje ich relację porządkowania, wyrażoną jako bitowa lub tych stałych, zdefiniowaną w math.h:

| Wartość | Opis |
|------------|-----------------|
| **_FP_LT** | *x* można uznać za mniej niż *y* |
| **_FP_EQ** | *x* można uznać za równe *y* |
| **_FP_GT** | *x* można uznać za większe niż *y* |

Te prymitywy implementują [isgreater, isgreaterequal, isless, islessequal, islessgreater i isunordered](floating-point-ordering.md) makr i funkcji w CRT.

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

Te prymitywy zmiennoprzecinowe implementują wersje C++ funkcji CRT [fpclassify](fpclassify.md) dla typów zmiennoprzecinkowych. Argument *x* jest oceniany, a klasyfikacja jest zwracana jako jedna z tych stałych, zdefiniowana w pliku math.h:

|Wartość|Opis|
|-----------|-----------------|
| **FP_NAN** | Cichy, sygnalizujący lub nieokreślony NaN |
| **FP_INFINITE** | Dodatnia lub ujemna nieskończoność |
| **FP_NORMAL** | Dodatnia lub ujemna znormalizowana wartość niezerowa |
| **FP_SUBNORMAL** | Dodatnia lub ujemna wartość subnormal (zdenormalowana) |
| **FP_ZERO** | Dodatnia lub ujemna wartość zerowa |

Aby uzyskać dodatkowe informacje, można użyć [funkcji _fpclass, _fpclassf](fpclass-fpclassf.md) specyficznych dla firmy Microsoft. Użyj funkcji [fpclassify, aby](fpclassify.md) uzyskać przenośność.

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

*Exp*<br/>
Wykładnik jako typ integralny.

### <a name="remarks"></a>Uwagi

Te prymitywy zmiennoprzecinkowe przyjmują wskaźnik do wartości zmiennoprzecinkowej *px* i *exp*wartości wykładniczej i usuwają ułamkową część wartości zmiennoprzecinkowej poniżej podanego wykładnika, jeśli to możliwe. Zwracana wartość jest wynikiem **fpclassify** na wartości wejściowej w *px,* jeśli jest NaN lub nieskończoności i na wartość danych wyjściowych w *px* w przeciwnym razie.

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

*Exp*<br/>
Wykładnik jako typ integralny.

### <a name="remarks"></a>Uwagi

Te prymitywy zmiennoprzecinkowe przyjmują wskaźnik do wartości zmiennoprzecinkowej *px* i wartość wykładniczą *exp*i skalują wartość w *px* o 2<sup>*exp,*</sup>jeśli to możliwe. Zwracana wartość jest wynikiem **fpclassify** na wartości wejściowej w *px,* jeśli jest NaN lub nieskończoności i na wartość danych wyjściowych w *px* w przeciwnym razie. Dla przenośności, wolą [ldexp, ldexpf i ldexpl](ldexp.md) funkcji.

## <a name="_dunscale-_ldunscale-_fdunscale"></a>_dunscale, _ldunscale, _fdunscale

### <a name="syntax"></a>Składnia

```C
short __cdecl _dunscale(short* pexp, double* px);
short __cdecl _ldunscale(short* pexp, long double* px);
short __cdecl _fdunscale(short* pexp, float* px);
```

### <a name="parameters"></a>Parametry

*pexp (pexp)*<br/>
Wskaźnik do wykładnika jako typu integralnego.

*piks.*<br/>
Wskaźnik do argumentu zmiennoprzecinkowego.

### <a name="remarks"></a>Uwagi

Te prymitywy zmiennoprzecinkowe rozkładają wartość zmiennoprzecinkową wskazywal przez *px* na significand (mantissa) i wykładnik, jeśli to możliwe. Significand jest skalowany w taki sposób, że wartość bezwzględna jest większa lub równa 0,5 i mniej niż 1,0. Wykładnik jest wartością *n*, gdzie oryginalna wartość zmiennoprzecinkowy jest równa skalowane significand razy 2<sup>*n*</sup>. Ten wykładnik liczby całkowitej *n* jest przechowywany w lokalizacji wskazanej przez *pexp*. Zwracana wartość jest wynikiem **fpclassify** na wartości wejściowej w *px,* jeśli jest NaN lub nieskończoności, a na wartość danych wyjściowych w przeciwnym razie. Dla przenośności, wolą [frexp, frexpf, frexpl](frexp.md) funkcji.

## <a name="_dexp-_ldexp-_fdexp"></a>_dexp, _ldexp, _fdexp

### <a name="syntax"></a>Składnia

```C
short __cdecl _dexp(double* px, double y, long exp);
short __cdecl _ldexp(long double* px, long double y, long exp);
short __cdecl _fdexp(float* px, float y, long exp);
```

### <a name="parameters"></a>Parametry

*Y*<br/>
Argument funkcji zmiennoprzecinowej.

*piks.*<br/>
Wskaźnik do argumentu zmiennoprzecinkowego.

*Exp*<br/>
Wykładnik jako typ integralny.

### <a name="remarks"></a>Uwagi

Te prymitywy zmiennoprzecinające tworzą wartość zmiennoprzecinkową w lokalizacji wskazywowej przez *px* równą *y* * 2<sup>*exp*</sup>. Zwracana wartość jest wynikiem **fpclassify** na wartości wejściowej w *y,* jeśli jest ToNa lub nieskończoności, a na wartość wyjściową w *px* w przeciwnym razie. Dla przenośności, wolą [ldexp, ldexpf i ldexpl](ldexp.md) funkcji.

## <a name="_dnorm-_fdnorm"></a>_dnorm, _fdnorm

### <a name="syntax"></a>Składnia

```C
short __cdecl _dnorm(unsigned short* ps);
short __cdecl _fdnorm(unsigned short* ps);
```

### <a name="parameters"></a>Parametry

*Ps*<br/>
Wskaźnik do bitowej reprezentacji wartości zmiennoprzecinkowej wyrażonej jako **tablica niepodpisanego** **krótkiego**.

### <a name="remarks"></a>Uwagi

Te prymitywy zmiennoprzecinkowe normalizują ułamkową część niedopełnionej wartości zmiennoprzecinkowej i dostosowują *charakterystykę*lub tendencyjny wykładnik, aby dopasować. Wartość jest przekazywana jako bitowa reprezentacja typu zmiennoprzecinkowego konwertowana `_float_val` na tablicę **niepodpisaną** **krótką** przez `_double_val` `_ldouble_val`, lub typ punning union zadeklarowany w math.h. Zwracana wartość jest wynikiem **fpclassify** na wejściowej wartości zmiennoprzecinkowej, jeśli jest Tona lub nieskończoności, a na wartość danych wyjściowych w przeciwnym razie.

## <a name="_dpoly-_ldpoly-_fdpoly"></a>_dpoly, _ldpoly, _fdpoly

### <a name="syntax"></a>Składnia

```C
double __cdecl _dpoly(double x, double const* table, int n);
long double __cdecl _ldpoly(long double x, long double const* table, int n);
float __cdecl _fdpoly(float x, _float const* table, int n);
```

### <a name="parameters"></a>Parametry

*X*<br/>
Argument funkcji zmiennoprzecinowej.

*table*<br/>
Wskaźnik do tabeli stałych współczynników wielomianowych.

*N*<br/>
Kolejność wielomianu do oceny.

### <a name="remarks"></a>Uwagi

Te prymitywy zmiennoprzecinkowe zwracają ocenę *x* w wielomianowym rzędu *n,* którego współczynniki są reprezentowane przez odpowiadające im wartości stałe w *tabeli*. Na przykład, jeśli *tabela*\[0] = 3,0, *tabela*\[1] = 4,0, *tabela*\[2] = 5,0 i *n* = 2, reprezentuje wielomian 5,0x<sup>2</sup> + 4,0x + 3,0. Jeśli ten wielomian jest oceniany dla *x* 2.0, wynik wynosi 31,0. Te funkcje nie są używane wewnętrznie.

## <a name="_dlog-_dlog-_dlog"></a>_dlog, _dlog, _dlog

### <a name="syntax"></a>Składnia

```C
double __cdecl _dlog(double x, int base_flag);
long double __cdecl _ldlog(long double x, int base_flag);
float __cdecl _fdlog(float x, int base_flag);
```

### <a name="parameters"></a>Parametry

*X*<br/>
Argument funkcji zmiennoprzecinowej.

*base_flag*<br/>
Flaga, która steruje bazą do użycia, 0 dla bazy *e* i niezerowa dla podstawy 10.

### <a name="remarks"></a>Uwagi

Te prymitywy zmiennoprzecinowe zwracają dziennik naturalny *x*, ln(*x*) lub log<sub>*e*</sub>(*x*), gdy *base_flag* wynosi 0. Zwracają podstawę dziennika 10 *x*lub dziennik<sub>10</sub>*(x),* gdy *base_flag* jest niezerowy. Te funkcje nie są używane wewnętrznie. Aby uzyskać przenośność, preferuj [funkcje log, logf, logl, log10, log10f i log10l](log-logf-log10-log10f.md).

## <a name="_dsin-_ldsin-_fdsin"></a>_dsin, _ldsin, _fdsin

### <a name="syntax"></a>Składnia

```C
double __cdecl _dsin(double x, unsigned int quadrant);
long double __cdecl _ldsin(long double x, unsigned int quadrant);
float __cdecl _fdsin(float x, unsigned int quadrant);
```

### <a name="parameters"></a>Parametry

*X*<br/>
Argument funkcji zmiennoprzecinowej.

*Kwadrant*<br/>
Przesunięcie kwadrantu 0, 1, 2 lub `sin`3 `-sin`do `-cos` użycia do wytwarzania `cos`, i wyniki.

### <a name="remarks"></a>Uwagi

Te prymitywy zmiennoprzecinowe zwracają sinus *x* odsunięty przez *modulo kwadrantu* 4. Skutecznie zwracają sinusoidę, cosine, -sine i -cosine *x,* gdy *modulo kwadrantu* 4 wynosi odpowiednio 0, 1, 2 lub 3. Te funkcje nie są używane wewnętrznie. Dla przenośności, wolą [grzech, sinf, sinl](sin-sinf-sinl.md), [cos, cosf i cosl](cos-cosf-cosl.md) funkcji.

## <a name="requirements"></a>Wymagania

Nagłówek: \<math.h>

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Obsługa liczb zmiennoprzecinkowych](../floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
[cos, cosf, cosl](cos-cosf-cosl.md)<br/>
[frexp, frexpf, frexpl](frexp.md)<br/>
[ldexp, ldexpf i ldexpl](ldexp.md)<br/>
[log, logf, logl, log10, log10f, log10l](log-logf-log10-log10f.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
