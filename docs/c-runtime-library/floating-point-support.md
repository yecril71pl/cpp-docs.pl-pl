---
title: Matematyczne i Obsługa liczb zmiennoprzecinkowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/06/2018
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.math
dev_langs:
- C++
helpviewer_keywords:
- floating-point numbers, math routines
- math routines
- floating-point numbers
ms.assetid: e4fcaf69-5c8e-4854-a9bb-1f412042131e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ddf4a6ce7e2ad98841c20fcef5fd9639a5797852
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="math-and-floating-point-support"></a>Matematyczne i Obsługa liczb zmiennoprzecinkowych

Universal C Runtime library (Biblioteka UCRT) zawiera wiele funkcji biblioteki matematyczne całkowitych i zmiennoprzecinkowych, wraz ze wszystkimi wymaganymi przez ISO C99. Funkcje liczb zmiennoprzecinkowych są implementowane w celu zrównoważenia wydajności z poprawności. Ponieważ produkujących poprawnie zaokrąglony wynik może być zbyt duży, te funkcje są przeznaczone do wydajnie tworzyć Zamknij zbliżenia się poprawnie zaokrąglony wynik. W większości przypadków wyniku zwracany znajduje się w +/-1 ulp poprawnie zaokrąglony wyniku, chociaż może się zdarzyć, gdy istnieje większej dokładności.

Liczby zmiennoprzecinkowe punktu funkcje biblioteki matematyczne mają różne implementacje dla innej architektury Procesora. Na przykład x86 32-bitowych CRT może mieć inną implementację niż x64 64-bitowych CRT. Ponadto niektóre funkcje mogą mieć wiele implementacji dla danej architektury Procesora. Najbardziej efektywne implementacji wybrano dynamicznie w czasie wykonywania w zależności od zbiór instrukcji obsługiwane przez procesor CPU. Na przykład w 32-bitowych x86 CRT, niektóre funkcje mają zarówno x87 implementacji i implementację SSE2. Podczas uruchamiania na procesora CPU obsługującego usługę SSE2, szybsze implementacji SSE2 jest używany. Podczas uruchamiania na Procesorze, który nie obsługuje SSE2, wolniejsze x87 implementacji jest używana. Ponieważ różnych implementacji funkcji biblioteki matematyczne mogą używać różnych instrukcji procesora CPU i różnych algorytmów w celu uzyskania ich wyników, funkcje może wygenerować różne wyniki we wszystkich procesorach. W większości przypadków wyniki są w +/-1 ulp poprawnie zaokrąglony wyniku, ale na rzeczywistą wydajność może się różnić we wszystkich procesorach.

Poprzednich wersji 16-bitowych Microsoft C/C++ i Microsoft Visual C++ obsługiwane **podwójnej długości** typ jako typ danych liczb zmiennoprzecinkowych 80 bitowa precyzja. W nowszych wersjach programu Visual C++ **podwójnej długości** — typ danych jest taki sam jak typ danych liczb zmiennoprzecinkowych 64-bitowa precyzja **podwójne** typu. Kompilator traktuje **podwójnej długości** i **podwójne** jako różne typy, ale **podwójnej długości** funkcje są takie same jak ich **podwójne** odpowiedniki. Udostępnia CRT **podwójnej długości** wersji funkcje matematyczne dla ISO C99 zgodnością kodu źródłowego, ale należy pamiętać, że reprezentacja binarna może różnić się od inne kompilatory.

## <a name="supported-math-and-floating-point-routines"></a>Obsługiwane matematyczne i procedury liczb zmiennoprzecinkowych

|Procedura|Zastosowanie|
|-|-|
[abs, labs, llabs, _abs64](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|Oblicza wartość bezwzględna typu Liczba całkowita
[acos, acosf, acosl](../c-runtime-library/reference/acos-acosf-acosl.md)|Oblicza arcus cosinus
[acosh, acoshf, acoshl](../c-runtime-library/reference/acosh-acoshf-acoshl.md)|Oblicza cosinus hiperboliczny łuk
[asin, asinf, asinl](../c-runtime-library/reference/asin-asinf-asinl.md)|Oblicza sinus łuk
[asinh, asinhf, asinhl](../c-runtime-library/reference/asinh-asinhf-asinhl.md)|Oblicza sinus hiperboliczny łuk
[atan, atanf, atanl, atan2, atan2f, atan2l](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|Oblicza arcus tangens
[atanh, atanhf, atanhl](../c-runtime-library/reference/atanh-atanhf-atanhl.md)|Oblicza tangens hiperboliczny łuk
[_atodbl —, _atodbl_l —](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|Konwertuje ciąg ustawień regionalnych **podwójne**
[atof, _atof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Konwertuje ciąg na **podwójne**
[_atoflt, _atoflt_l, _atoldbl, _atoldbl_l](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|Konwertuje ciąg ustawień regionalnych **float** lub **podwójnej długości**
[cbrt, cbrtf, cbrtl](../c-runtime-library/reference/cbrt-cbrtf-cbrtl.md)|Oblicza pierwiastek modułu
[ceil, ceilf, ceill](../c-runtime-library/reference/ceil-ceilf-ceill.md)|Oblicza Zaokrąglenie w górę
[_chgsign, _chgsignf, _chgsignl](../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)|Oblicza odwrotność dodatku
[_clear87, _clearfp](../c-runtime-library/reference/clear87-clearfp.md)|Pobiera i usuwa z rejestru stanu liczb zmiennoprzecinkowych
[_control87 —, \__control87_2, _controlfp —](../c-runtime-library/reference/control87-controlfp-control87-2.md)|Pobiera i ustawia słowa formantu liczb zmiennoprzecinkowych
[_controlfp_s](../c-runtime-library/reference/controlfp-s.md)|Bezpieczna wersja **_controlfp —**
[copysign, copysignf, copysignl, _copysign, _copysignf, _copysignl](../c-runtime-library/reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)|Zwraca wartość, która ma wielkość jednego argumentu i logowania innego
[COS cosf —, cosl —](../c-runtime-library/reference/cos-cosf-cosl.md)|Oblicza sinus
[cosh, coshf, coshl](../c-runtime-library/reference/cosh-coshf-coshl.md)|Oblicza sinus hiperboliczny
[DIV ldiv —, lldiv —](../c-runtime-library/reference/div.md)|Oblicza iloraz i pozostałej części dwóch wartości całkowitych
[_ecvt —](../c-runtime-library/reference/ecvt.md), [ecvt —](../c-runtime-library/reference/posix-ecvt.md)|Konwertuje **podwójne** na ciąg
[_ecvt_s](../c-runtime-library/reference/ecvt-s.md)|Bezpieczna wersja **_ecvt —**
[ERF erff —, erfl —](../c-runtime-library/reference/erf-erff-erfl-erfc-erfcf-erfcl.md)|Oblicza funkcji błędu
[ERFC erfcf —, erfcl](../c-runtime-library/reference/erf-erff-erfl-erfc-erfcf-erfcl.md)|Oblicza funkcji uzupełniające błędu
[exp, expf, expl](../c-runtime-library/reference/exp-expf.md)|Oblicza wykładniczej *e*<sup>x</sup>
[exp2, exp2f, exp2l](../c-runtime-library/reference/exp2-exp2f-exp2l.md)|Oblicza wykładniczej 2<sup>x</sup>
[expm1, expm1f, expm1l](../c-runtime-library/reference/expm1-expm1f-expm1l.md)|Oblicza *e*<sup>x</sup>-1
[fabs, fabsf, fabsl](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|Oblicza wartość bezwzględną liczby typ zmiennoprzecinkowy
[_fcvt —](../c-runtime-library/reference/fcvt.md), [fcvt —](../c-runtime-library/reference/posix-fcvt.md)|Konwertuje ciąg liczba zmiennoprzecinkowa
[_fcvt_s](../c-runtime-library/reference/fcvt-s.md)|Bezpieczna wersja **_fcvt —**
[fdim, fdimf, fdiml](../c-runtime-library/reference/fdim-fdimf-fdiml.md)|Określa dodatnią różnicę między dwiema wartościami
[feclearexcept](../c-runtime-library/reference/feclearexcept1.md)|Czyści określone wyjątki zmiennoprzecinkowe
[fegetenv](../c-runtime-library/reference/fegetenv1.md)|Zapisuje bieżące środowisko liczb zmiennoprzecinkowych
[fegetexceptflag](../c-runtime-library/reference/fegetexceptflag2.md)|Pobiera stan określony wyjątek zmiennoprzecinkowy
[fegetround](../c-runtime-library/reference/fegetround-fesetround2.md)|Pobiera tryb zaokrąglania liczb zmiennoprzecinkowych
[feholdexcept](../c-runtime-library/reference/feholdexcept2.md)|Ustawia tryb-stop zmiennoprzecinkowych wyjątków
[feraiseexcept](../c-runtime-library/reference/feraiseexcept.md)|Wywołuje określone wyjątki zmiennoprzecinkowe
[fesetenv](../c-runtime-library/reference/fesetenv1.md)|Ustawia bieżącego środowiska liczb zmiennoprzecinkowych
[fesetexceptflag](../c-runtime-library/reference/fesetexceptflag2.md)|Ustawia flagi określony stan liczb zmiennoprzecinkowych
[fesetround](../c-runtime-library/reference/fegetround-fesetround2.md)|Ustawia określony tryb zaokrąglania liczb zmiennoprzecinkowych
[fetestexcept](../c-runtime-library/reference/fetestexcept1.md)|Określa flag stanu zmiennoprzecinkowych wyjątków, które są ustawione
[feupdateenv](../c-runtime-library/reference/feupdateenv.md)|Przywraca środowisko liczb zmiennoprzecinkowych, a następnie wywołuje poprzedniej wyjątków
[_finite, _finitef](../c-runtime-library/reference/finite-finitef.md)|Określa, czy wartość jest wartością skończoną
[floor, floorf, floorl](../c-runtime-library/reference/floor-floorf-floorl.md)|Oblicza Zaokrąglenie w dół
[fma, fmaf, fmal](../c-runtime-library/reference/fma-fmaf-fmal.md)|Oblicza kolei mnożeniem
[fmax, fmaxf, fmaxl](../c-runtime-library/reference/fmax-fmaxf-fmaxl.md)|Oblicza maksymalną liczbę argumentów
[fmin, fminf, fminl](../c-runtime-library/reference/fmin-fminf-fminl.md)|Oblicza minimalną argumentów
[fmod —, fmodf —, fmodl](../c-runtime-library/reference/fmod-fmodf.md)|Oblicza resztę liczb zmiennoprzecinkowych
[_fpclass, _fpclassf](../c-runtime-library/reference/fpclass-fpclassf.md)|Zwraca wartość zmiennoprzecinkową klasyfikacji
[fpclassify](../c-runtime-library/reference/fpclassify.md)|Zwraca wartość zmiennoprzecinkową klasyfikacji
[_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md)|Ustawia program obsługi wyjątki zmiennoprzecinkowe
[_fpreset](../c-runtime-library/reference/fpreset.md)|Przywraca środowisko liczb zmiennoprzecinkowych
[frexp —, frexpf —, frexpl —](../c-runtime-library/reference/frexp.md)|Pobiera mantysa i wykładnik liczby zmiennoprzecinkowe
[_gcvt —](../c-runtime-library/reference/gcvt.md), [gcvt —](../c-runtime-library/reference/posix-gcvt.md)|Konwertuje ciąg liczba zmiennoprzecinkowa
[_gcvt_s](../c-runtime-library/reference/gcvt-s.md)|Bezpieczna wersja **_gcvt —**
[_get_FMA3_enable, _set_FMA3_enable](../c-runtime-library/reference/get-fma3-enable-set-fma3-enable.md)|Pobiera lub ustawia flagę do użytku w instrukcji FMA3 x64
[hypot, hypotf, hypotl, _hypot, _hypotf, _hypotl](../c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md)|Oblicza przeciwprostokątnej
[ilogb, ilogbf, ilogbl](../c-runtime-library/reference/ilogb-ilogbf-ilogbl2.md)|Oblicza wykładnik base-2 liczba całkowita
[imaxabs](../c-runtime-library/reference/imaxabs.md)|Oblicza wartość bezwzględna typu Liczba całkowita
[imaxdiv](../c-runtime-library/reference/imaxdiv.md)|Oblicza iloraz i pozostałej części dwóch wartości całkowitych
[isnan, _isnan, _isnanf](../c-runtime-library/reference/isnan-isnan-isnanf.md)|Testów zmiennoprzecinkowych wartości NaN
[_j0, _j1, _jn](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|Oblicza funkcji Bessela
[ldexp —, ldexpf —, ldexpl](../c-runtime-library/reference/ldexp.md)|Oblicza x * 2<sup>n</sup>
[lgamma, lgammaf, lgammal](../c-runtime-library/reference/lgamma-lgammaf-lgammal.md)|Oblicza logarytm naturalny wartość bezwzględną liczby funkcji gamma
[llrint llrintf, llrintl](../c-runtime-library/reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)|Zaokrągla wartość zmiennoprzecinkowa do najbliższej **długi czas** wartość
[llround —, llroundf —, llroundl —](../c-runtime-library/reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md)|Zaokrągla wartość zmiennoprzecinkowa do najbliższej **długi czas** wartość
[Dziennik, logf —, logl, log10 log10f —, log10l](../c-runtime-library/reference/log-logf-log10-log10f.md)|Oblicza logarytm fizyczną lub base-10
[log1p —, log1pf —, log1pl](../c-runtime-library/reference/log1p-log1pf-log1pl2.md)|Oblicza logarytm naturalny 1 + x
[log2, log2f, log2l](../c-runtime-library/reference/log2-log2f-log2l.md)|Oblicza logarytm base-2
[logb, logbf, logbl, _logb, _logbf](../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)|Zwraca wykładnik liczb zmiennoprzecinkowych wartości
[lrint lrintf, lrintl](../c-runtime-library/reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)|Zaokrągla wartość zmiennoprzecinkowa do najbliższej **długi** wartość
[_lrotl, _lrotr](../c-runtime-library/reference/lrotl-lrotr.md)|Obraca wartość całkowitą w lewo lub w prawo
[lround —, lroundf —, lroundl —](../c-runtime-library/reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md)|Zaokrągla wartość zmiennoprzecinkowa do najbliższej **długi** wartość
[_matherr](../c-runtime-library/reference/matherr.md)|Błąd matematyczny domyślny program obsługi
[__max](../c-runtime-library/reference/max.md)|Makra, które zwraca większy z dwóch wartości
[__min](../c-runtime-library/reference/min.md)|Makra, która zwraca mniejszy z dwóch wartości
[modf, modff, modfl](../c-runtime-library/reference/modf-modff-modfl.md)|Dzieli wartości zmiennoprzecinkowej w ułamkowa i części liczba całkowita
[nan, nanf, nanl](../c-runtime-library/reference/nan-nanf-nanl.md)|Zwraca wartość NaN quiet
[nearbyint —, nearbyintf —, nearbyintl](../c-runtime-library/reference/nearbyint-nearbyintf-nearbyintl1.md)|Zwraca wartość zaokrąglony
[nextafter — nextafterf —, nextafterl, _nextafter —, _nextafterf](../c-runtime-library/reference/nextafter-functions.md)|Zwraca następnej można przedstawić wartości zmiennoprzecinkowych
[nexttoward nexttowardf, nexttowardl](../c-runtime-library/reference/nextafter-functions.md)|Zwraca następnej można przedstawić wartości zmiennoprzecinkowych
[pow, powf, powl](../c-runtime-library/reference/pow-powf-powl.md)|Zwraca wartość *x*<sup>*y*</sup>
[remainder, remainderf, remainderl](../c-runtime-library/reference/remainder-remainderf-remainderl.md)|Oblicza w pozostałej części iloraz dwóch wartości zmiennoprzecinkowych
[remquo, remquof, remquol](../c-runtime-library/reference/remquo-remquof-remquol.md)|Oblicza resztę z dwóch wartości całkowitych
[rint, rintf, rintl](../c-runtime-library/reference/rint-rintf-rintl.md)|Zaokrągla wartość zmiennoprzecinkowa
[_rotl, _rotl64, _rotr, _rotr64](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|Obracanie bitów typów całkowitych
[round, roundf, roundl](../c-runtime-library/reference/round-roundf-roundl.md)|Zaokrągla wartość zmiennoprzecinkowa
[_scalb —, _scalbf](../c-runtime-library/reference/scalb.md)|Skaluje argumentu przez potęgą liczby 2
[scalbn, scalbnf, scalbnl, scalbln, scalblnf, scalblnl](../c-runtime-library/reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md)|Mnoży liczba zmiennoprzecinkowa przez całkowitą potęgą liczby **flt_radix —**
[_set_controlfp](../c-runtime-library/reference/set-controlfp.md)|Ustawia słowa formantu liczb zmiennoprzecinkowych
[_set_SSE2_enable](../c-runtime-library/reference/set-sse2-enable.md)|Włącza lub wyłącza instrukcje SSE2
[sin, sinf, sinl](../c-runtime-library/reference/sin-sinf-sinl.md)|Oblicza sinus
[sinh, sinhf, sinhl](../c-runtime-library/reference/sinh-sinhf-sinhl.md)|Oblicza sinus hiperboliczny
[sqrt, sqrtf, sqrtl](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|Oblicza pierwiastek kwadratowy
[_status87, _statusfp, _statusfp2](../c-runtime-library/reference/status87-statusfp-statusfp2.md)|Pobiera słowa stanu liczb zmiennoprzecinkowych
[strtof, _strtof_l](../c-runtime-library/reference/strtof-strtof-l-wcstof-wcstof-l.md)|Konwertuje ciąg na **liczb zmiennoprzecinkowych**
[strtold, _strtold_l](../c-runtime-library/reference/strtold-strtold-l-wcstold-wcstold-l.md)|Konwertuje ciąg na **długi** **podwójne**
[tan, tanf, tanl](../c-runtime-library/reference/tan-tanf-tanl.md)|Oblicza tangens
[tanh, tanhf, tanhl](../c-runtime-library/reference/tanh-tanhf-tanhl.md)|Oblicza tangens hiperboliczny
[tgamma, tgammaf, tgammal](../c-runtime-library/reference/tgamma-tgammaf-tgammal.md)|Oblicza funkcji gamma
[trunc, truncf, truncl](../c-runtime-library/reference/trunc-truncf-truncl.md)|Obcina część ułamkowa
[_wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Konwertuje ciąg typu wide do **podwójne**
[_y0, _y1, _yn](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|Oblicza funkcji Bessela

## <a name="see-also"></a>Zobacz także

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
