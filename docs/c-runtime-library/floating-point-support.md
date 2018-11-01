---
title: Matematyczne i Obsługa liczb zmiennoprzecinkowych
ms.date: 04/06/2018
f1_keywords:
- c.math
helpviewer_keywords:
- floating-point numbers, math routines
- math routines
- floating-point numbers
ms.assetid: e4fcaf69-5c8e-4854-a9bb-1f412042131e
ms.openlocfilehash: 9e1baeb7236e5b1144b52df0bd83cc0f4a4b7796
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558239"
---
# <a name="math-and-floating-point-support"></a>Matematyczne i Obsługa liczb zmiennoprzecinkowych

Biblioteka uniwersalnego środowiska języka C (UCRT) zawiera wiele funkcji bibliotek matematycznych całkowite i zmiennoprzecinkowe, w tym wszystkie wymagane przez ISO C99. Funkcje liczb zmiennoprzecinkowych zostały zaimplementowane zrównoważyć wydajność za pomocą poprawności. Ponieważ tworzenie poprawnie zaokrąglony wynik może być zbyt duży, te funkcje są przeznaczone do wydajnego tworzenia bliskie zbliżenia wyniku poprawnie zaokrąglony. W większości przypadków wynik tworzony mieści się w +/-1 ulp poprawnie zaokrąglone wyniku, chociaż może się zdarzyć, gdy większej dokładności.

Liczby zmiennoprzecinkowej punktu funkcji bibliotek matematycznych mają różne implementacje dla innej architektury Procesora. Na przykład x86 32-bitowych CRT może mieć inną implementację od x64 64-bitowych CRT. Ponadto niektóre funkcje mogą mieć wiele implementacji dla danej architektury Procesora. Najbardziej efektywny sposób wdrażania jest wybierana dynamicznie w czasie wykonywania w zależności od zestawów instrukcji, obsługiwanych przez CPU. Na przykład w x86 32-bitowych CRT, niektóre funkcje mają zarówno x87 implementacji i implementację SSE2. Podczas uruchamiania, na którego procesor CPU obsługuje SSE2, szybsze implementacji SSE2 jest używany. Podczas uruchamiania na procesorze CPU, który nie obsługuje SSE2, wolniejsze x87 implementacja jest używana. Ponieważ różne implementacje funkcji bibliotek matematycznych może używać różne instrukcje procesora CPU i różnych algorytmów, aby wygenerować ich wyniki, funkcje mogą wygenerować różne wyniki we wszystkich procesorach. W większości przypadków wyniki znajdują się w +/-1 ulp poprawnie zaokrąglone wyników, ale rzeczywiste wyniki mogą się różnić we wszystkich procesorach.

Poprzednie 16-bitowymi wersjami Microsoft C/C++ i Microsoft Visual C++ obsługuje **typu long double** typ jako typ danych zmiennoprzecinkowych 80-bitowa precyzja. W nowszych wersjach programu Visual C++ **typu long double** typ danych jest taka sama jak typ danych zmiennopozycyjnych 64-bitowa precyzja **double** typu. Kompilator traktuje **typu long double** i **double** jako różne typy, ale **typu long double** funkcje są takie same jak ich **double** odpowiedniki. Udostępnia CRT **typu long double** wersje funkcji matematycznych ISO C99 zgodność kodu źródłowego, ale należy pamiętać, że reprezentacja binarna może różnić się od innych kompilatorów.

## <a name="supported-math-and-floating-point-routines"></a>Procedury zmiennoprzecinkowe i obsługiwanych matematyczne

|Procedura|Zastosowanie|
|-|-|
[abs, labs, llabs, _abs64](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|Oblicza wartość bezwzględną typu Liczba całkowita
[acos, acosf, acosl](../c-runtime-library/reference/acos-acosf-acosl.md)|Oblicza arcus cosinus
[acosh, acoshf, acoshl](../c-runtime-library/reference/acosh-acoshf-acoshl.md)|Oblicza arcus cosinus hiperboliczny
[asin, asinf, asinl](../c-runtime-library/reference/asin-asinf-asinl.md)|Oblicza arcus sinus
[asinh, asinhf, asinhl](../c-runtime-library/reference/asinh-asinhf-asinhl.md)|Oblicza arcus sinus hiperboliczny
[atan, atanf, atanl, atan2, atan2f, atan2l](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|Oblicza arcus tangens
[atanh, atanhf, atanhl](../c-runtime-library/reference/atanh-atanhf-atanhl.md)|Oblicza arcus tangens hiperboliczny
[_atodbl —, _atodbl_l —](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|Konwertuje ciąg na specyficzną dla ustawień regionalnych **double**
[atof, _atof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Konwertuje ciąg na **double**
[_atoflt, _atoflt_l, _atoldbl, _atoldbl_l](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|Konwertuje ciąg na specyficzną dla ustawień regionalnych **float** lub **typu long double**
[cbrt, cbrtf, cbrtl](../c-runtime-library/reference/cbrt-cbrtf-cbrtl.md)|Oblicza głównego modułu
[ceil, ceilf, ceill](../c-runtime-library/reference/ceil-ceilf-ceill.md)|Oblicza Zaokrąglenie w górę
[_chgsign, _chgsignf, _chgsignl](../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)|Oblicza odwrotność dodatku
[_clear87, _clearfp](../c-runtime-library/reference/clear87-clearfp.md)|Pobiera i usuwa z rejestru stanu zmiennoprzecinkowego
[_control87 —, \__control87_2, _controlfp](../c-runtime-library/reference/control87-controlfp-control87-2.md)|Pobiera i ustawia słowo sterujące zmiennoprzecinkowe
[_controlfp_s](../c-runtime-library/reference/controlfp-s.md)|Bezpieczna wersja **_controlfp**
[copysign, copysignf, copysignl, _copysign, _copysignf, _copysignl](../c-runtime-library/reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)|Zwraca wartość, która ma wielkość jednego z argumentów i znak innego
[COS cosf —, cosl —](../c-runtime-library/reference/cos-cosf-cosl.md)|Oblicza sinus
[cosh, coshf, coshl](../c-runtime-library/reference/cosh-coshf-coshl.md)|Oblicza sinus hiperboliczny
[DIV ldiv, lldiv](../c-runtime-library/reference/div.md)|Oblicza iloraz i resztę dwóch liczb całkowitych
[_ecvt —](../c-runtime-library/reference/ecvt.md), [ecvt —](../c-runtime-library/reference/posix-ecvt.md)|Konwertuje **double** na ciąg
[_ecvt_s](../c-runtime-library/reference/ecvt-s.md)|Bezpieczna wersja **_ecvt —**
[ERF erff —, erfl —](../c-runtime-library/reference/erf-erff-erfl-erfc-erfcf-erfcl.md)|Oblicza funkcję błędu
[ERFC erfcf —, erfcl](../c-runtime-library/reference/erf-erff-erfl-erfc-erfcf-erfcl.md)|Oblicza komplementarną funkcję błędu
[exp, expf, expl](../c-runtime-library/reference/exp-expf.md)|Oblicza wartość wykładniczą *e*<sup>x</sup>
[exp2, exp2f, exp2l](../c-runtime-library/reference/exp2-exp2f-exp2l.md)|Oblicza wartość wykładniczą 2<sup>x</sup>
[expm1, expm1f, expm1l](../c-runtime-library/reference/expm1-expm1f-expm1l.md)|Oblicza *e*<sup>x</sup>-1
[fabs, fabsf, fabsl](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|Oblicza wartość bezwzględną typu zmiennoprzecinkowego
[_fcvt —](../c-runtime-library/reference/fcvt.md), [fcvt —](../c-runtime-library/reference/posix-fcvt.md)|Konwertuje liczbę zmiennoprzecinkową
[_fcvt_s](../c-runtime-library/reference/fcvt-s.md)|Bezpieczna wersja **_fcvt —**
[fdim, fdimf, fdiml](../c-runtime-library/reference/fdim-fdimf-fdiml.md)|Określa dodatnią różnicę między dwiema wartościami
[feclearexcept](../c-runtime-library/reference/feclearexcept1.md)|Czyści określone wyjątki zmiennoprzecinkowe
[fegetenv](../c-runtime-library/reference/fegetenv1.md)|Zapisuje bieżące środowisko zmiennoprzecinkowych
[fegetexceptflag](../c-runtime-library/reference/fegetexceptflag2.md)|Pobiera stan określonego wyjątku zmiennoprzecinkowego
[fegetround](../c-runtime-library/reference/fegetround-fesetround2.md)|Pobiera zmiennoprzecinkowe trybu zaokrąglania
[feholdexcept](../c-runtime-library/reference/feholdexcept2.md)|Ustawia tryb wyjątków zmiennoprzecinkowych-stop
[feraiseexcept](../c-runtime-library/reference/feraiseexcept.md)|Wywołuje określone wyjątki zmiennoprzecinkowe
[fesetenv](../c-runtime-library/reference/fesetenv1.md)|Ustawia bieżące środowisko zmiennoprzecinkowych
[fesetexceptflag](../c-runtime-library/reference/fesetexceptflag2.md)|Ustawia flagi określonego stanu zmiennoprzecinkowego
[fesetround](../c-runtime-library/reference/fegetround-fesetround2.md)|Ustawia określony tryb zaokrąglania zmiennoprzecinkowych
[fetestexcept](../c-runtime-library/reference/fetestexcept1.md)|Określa, które wyjątek zmiennoprzecinkowy, którego stan flagi są ustawione
[feupdateenv](../c-runtime-library/reference/feupdateenv.md)|Przywraca środowisko zmiennoprzecinkowych, a następnie zgłasza wyjątki poprzedniej
[_finite, _finitef](../c-runtime-library/reference/finite-finitef.md)|Określa, czy wartość jest wartością skończoną
[floor, floorf, floorl](../c-runtime-library/reference/floor-floorf-floorl.md)|Oblicza Zaokrąglenie w dół
[fma, fmaf, fmal](../c-runtime-library/reference/fma-fmaf-fmal.md)|Oblicza kolei mnożeniem
[fmax, fmaxf, fmaxl](../c-runtime-library/reference/fmax-fmaxf-fmaxl.md)|Oblicza maksymalną liczbę argumentów
[fmin, fminf, fminl](../c-runtime-library/reference/fmin-fminf-fminl.md)|Oblicza minimalna argumentów
[fmod, fmodf —, fmodl](../c-runtime-library/reference/fmod-fmodf.md)|Oblicza zmiennoprzecinkową resztę
[_fpclass, _fpclassf](../c-runtime-library/reference/fpclass-fpclassf.md)|Zwraca wartość zmiennoprzecinkową klasyfikacji
[fpclassify](../c-runtime-library/reference/fpclassify.md)|Zwraca wartość zmiennoprzecinkową klasyfikacji
[_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md)|Ustawia program obsługi wyjątków zmiennoprzecinkowych
[_fpreset](../c-runtime-library/reference/fpreset.md)|Resetuje środowisko, zmiennoprzecinkowych
[frexp —, frexpf —, frexpl —](../c-runtime-library/reference/frexp.md)|Pobiera mantysę i wykładnik liczba zmiennoprzecinkowa
[_gcvt —](../c-runtime-library/reference/gcvt.md), [gcvt —](../c-runtime-library/reference/posix-gcvt.md)|Konwertuje liczbę zmiennoprzecinkową
[_gcvt_s](../c-runtime-library/reference/gcvt-s.md)|Bezpieczna wersja **_gcvt —**
[_get_FMA3_enable, _set_FMA3_enable](../c-runtime-library/reference/get-fma3-enable-set-fma3-enable.md)|Pobiera lub ustawia flagę na używanie instrukcji FMA3 x64
[hypot, hypotf, hypotl, _hypot, _hypotf, _hypotl](../c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md)|Oblicza przeciwprostokątną
[ilogb, ilogbf, ilogbl](../c-runtime-library/reference/ilogb-ilogbf-ilogbl2.md)|Oblicza wykładnik base 2 liczba całkowita
[imaxabs](../c-runtime-library/reference/imaxabs.md)|Oblicza wartość bezwzględną typu Liczba całkowita
[imaxdiv](../c-runtime-library/reference/imaxdiv.md)|Oblicza iloraz i resztę dwóch liczb całkowitych
[isnan, _isnan, _isnanf](../c-runtime-library/reference/isnan-isnan-isnanf.md)|Sprawdza czy wartość zmiennoprzecinkowa NaN
[_j0, _j1, _jn](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|Oblicza wartość funkcji Bessela
[ldexp —, ldexpf —, ldexpl](../c-runtime-library/reference/ldexp.md)|Oblicza x * 2<sup>n</sup>
[lgamma, lgammaf, lgammal](../c-runtime-library/reference/lgamma-lgammaf-lgammal.md)|Oblicza wartość bezwzględną liczby funkcja gamma logarytm naturalny
[llrint llrintf, llrintl](../c-runtime-library/reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)|Zaokrągla wartość zmiennoprzecinkową do najbliższej **long long** wartość
[llround —, llroundf —, llroundl —](../c-runtime-library/reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md)|Zaokrągla wartość zmiennoprzecinkową do najbliższej **long long** wartość
[Dziennik, logf —, logl, log10 log10f —, log10l](../c-runtime-library/reference/log-logf-log10-log10f.md)|Oblicza logarytm naturalny lub base 10
[log1p —, log1pf —, log1pl](../c-runtime-library/reference/log1p-log1pf-log1pl2.md)|Oblicza logarytm naturalny 1 + x
[log2, log2f, log2l](../c-runtime-library/reference/log2-log2f-log2l.md)|Oblicza logarytm o podstawie 2 dla podanego
[logb, logbf, logbl, _logb, _logbf](../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)|Zwraca wykładnik liczb zmiennoprzecinkowych
[lrint lrintf, lrintl](../c-runtime-library/reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)|Zaokrągla wartość zmiennoprzecinkową do najbliższej **długie** wartość
[_lrotl, _lrotr](../c-runtime-library/reference/lrotl-lrotr.md)|Obraca się wartością całkowitą z zakresu w lewo lub w prawo
[lround —, lroundf —, lroundl —](../c-runtime-library/reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md)|Zaokrągla wartość zmiennoprzecinkową do najbliższej **długie** wartość
[_matherr](../c-runtime-library/reference/matherr.md)|Błąd matematyczny domyślny program obsługi
[__max](../c-runtime-library/reference/max.md)|Makro, które zwraca większy z dwóch wartości
[__min](../c-runtime-library/reference/min.md)|Makra, które zwraca mniejszy z dwóch wartości
[modf, modff, modfl](../c-runtime-library/reference/modf-modff-modfl.md)|Dzieli wartość zmiennoprzecinkowa do ułamkową i całkowitą części
[nan, nanf, nanl](../c-runtime-library/reference/nan-nanf-nanl.md)|Zwraca wartość NaN cichy
[nearbyint —, nearbyintf —, nearbyintl](../c-runtime-library/reference/nearbyint-nearbyintf-nearbyintl1.md)|Zwraca wartości zaokrąglony
[nextafter — nextafterf —, nextafterl, _nextafter —, _nextafterf](../c-runtime-library/reference/nextafter-functions.md)|Zwraca następną wartość zmiennoprzecinkowa
[nexttoward nexttowardf, nexttowardl](../c-runtime-library/reference/nextafter-functions.md)|Zwraca następną wartość zmiennoprzecinkowa
[pow, powf, powl](../c-runtime-library/reference/pow-powf-powl.md)|Zwraca wartość *x*<sup>*y*</sup>
[remainder, remainderf, remainderl](../c-runtime-library/reference/remainder-remainderf-remainderl.md)|Oblicza pozostałą część iloraz dwóch wartości zmiennoprzecinkowych
[remquo, remquof, remquol](../c-runtime-library/reference/remquo-remquof-remquol.md)|Oblicza pozostałą część dwóch wartości całkowitych
[rint, rintf, rintl](../c-runtime-library/reference/rint-rintf-rintl.md)|Zaokrągla wartość zmiennoprzecinkową
[_rotl, _rotl64, _rotr, _rotr64](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|Obracanie bitów typów całkowitych
[round, roundf, roundl](../c-runtime-library/reference/round-roundf-roundl.md)|Zaokrągla wartość zmiennoprzecinkową
[_scalb —, _scalbf](../c-runtime-library/reference/scalb.md)|Argument skali przez potęgą liczby 2
[scalbn, scalbnf, scalbnl, scalbln, scalblnf, scalblnl](../c-runtime-library/reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md)|Mnoży liczbę zmiennoprzecinkową przez całkowite możliwości **FLT_RADIX**
[_set_controlfp](../c-runtime-library/reference/set-controlfp.md)|Ustawia słowo sterujące zmiennoprzecinkowe
[_set_SSE2_enable](../c-runtime-library/reference/set-sse2-enable.md)|Włącza lub wyłącza instrukcje SSE2
[sin, sinf, sinl](../c-runtime-library/reference/sin-sinf-sinl.md)|Oblicza sinus
[sinh, sinhf, sinhl](../c-runtime-library/reference/sinh-sinhf-sinhl.md)|Oblicza sinus hiperboliczny
[sqrt, sqrtf, sqrtl](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|Oblicza pierwiastek kwadratowy
[_status87, _statusfp, _statusfp2](../c-runtime-library/reference/status87-statusfp-statusfp2.md)|Pobiera wyrazy stanu zmiennoprzecinkowe
[strtof, _strtof_l](../c-runtime-library/reference/strtof-strtof-l-wcstof-wcstof-l.md)|Konwertuje ciąg na **float**
[strtold, _strtold_l](../c-runtime-library/reference/strtold-strtold-l-wcstold-wcstold-l.md)|Konwertuje ciąg na **długie** **double**
[tan, tanf, tanl](../c-runtime-library/reference/tan-tanf-tanl.md)|Oblicza tangens
[tanh, tanhf, tanhl](../c-runtime-library/reference/tanh-tanhf-tanhl.md)|Oblicza tangens hiperboliczny
[tgamma, tgammaf, tgammal](../c-runtime-library/reference/tgamma-tgammaf-tgammal.md)|Oblicza funkcja gamma
[trunc, truncf, truncl](../c-runtime-library/reference/trunc-truncf-truncl.md)|Obcina część ułamkową
[_wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Konwertuje ciąg znaków dwubajtowych do **double**
[_y0, _y1, _yn](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|Oblicza wartość funkcji Bessela

## <a name="see-also"></a>Zobacz także

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
