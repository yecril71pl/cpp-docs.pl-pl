---
title: Obsługa obliczeń matematycznych i zmiennoprzecinkowych
ms.date: 01/31/2019
f1_keywords:
- c.math
helpviewer_keywords:
- floating-point numbers, math routines
- math routines
- floating-point numbers
ms.assetid: e4fcaf69-5c8e-4854-a9bb-1f412042131e
ms.openlocfilehash: ca1648719a4a98efc56ea3f543336b803c81c40f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226232"
---
# <a name="math-and-floating-point-support"></a>Obsługa obliczeń matematycznych i zmiennoprzecinkowych

Biblioteka uniwersalnego środowiska uruchomieniowego języka C (UCRT) udostępnia wiele prostych i zmiennoprzecinkowych funkcji biblioteki matematycznej, w tym wszystkie wymagane przez ISO C99. Funkcje zmiennoprzecinkowe są implementowane w celu zrównoważenia wydajności z korekcją. Ponieważ generowanie prawidłowo zaokrąglonego wyniku może być niezwykle kosztowne, te funkcje są zaprojektowane w celu wydajnego utworzenia bliskiego przybliżenia do prawidłowo zaokrąglonego wyniku. W większości przypadków powstaje wynik w zakresie od +/-1 ULP prawidłowo zaokrąglonego wyniku, chociaż mogą wystąpić sytuacje, w których występuje większa niedokładność.

Wiele funkcji wielozmiennoprzecinkowych bibliotek matematycznych ma różne implementacje dla różnych architektur procesora. Na przykład 32-bitowa architektura x86 CRT może mieć inną implementację niż 64-bit x64 CRT. Ponadto niektóre funkcje mogą mieć wiele implementacji dla danej architektury procesora CPU. Najbardziej wydajna implementacja jest wybierana dynamicznie w czasie wykonywania w zależności od zestawów instrukcji obsługiwanych przez procesor CPU. Na przykład w 32-bitowej architekturze x86, niektóre funkcje mają implementację x87 i implementację SSE2. W przypadku uruchamiania na PROCESORze, który obsługuje SSE2, używana jest szybsza implementacja SSE2. W przypadku uruchamiania na PROCESORze, który nie obsługuje SSE2, używana jest wolniejsza implementacja x87. Ponieważ różne implementacje funkcji biblioteki matematycznej mogą korzystać z różnych instrukcji procesora CPU i różnych algorytmów w celu wygenerowania ich wyników, funkcje mogą generować różne wyniki w procesorach. W większości przypadków wyniki znajdują się w przedziale od +/-1 ULP prawidłowo zaokrąglonego wyniku, ale rzeczywiste wyniki mogą się różnić w zależności od procesorów.

Poprzednie 16-bitowe wersje języka Microsoft C/C++ i Microsoft Visual C++ obsługują **`long double`** Typ danych zmiennoprzecinkowych o wartości 80-bitowej. W nowszych wersjach Visual C++ **`long double`** Typ danych to 64-bitowe precyzja typu danych, która jest identyczna z **`double`** typem. Kompilator traktuje **`long double`** i **`double`** jako różne typy, ale **`long double`** funkcje są identyczne z ich **`double`** odpowiednikami. CRT oferuje **`long double`** wersje funkcji matematycznych na potrzeby zgodności z kodem źródłowym ISO C99, ale zauważ, że reprezentacja binarna może się różnić od innych kompilatorów.

## <a name="supported-math-and-floating-point-routines"></a>Obsługiwane procedury matematyczne i zmiennoprzecinkowe

|Procedura|Zastosowanie|
|-|-|
[abs, labs, llabs, _abs64](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|Oblicza wartość bezwzględną typu Integer
[acos, acosf, acosl](../c-runtime-library/reference/acos-acosf-acosl.md)|Oblicza cosinus łuku
[acosh, acoshf, acoshl](../c-runtime-library/reference/acosh-acoshf-acoshl.md)|Oblicza cosinus łuku hiperbolicznego
[asin, asinf, asinl](../c-runtime-library/reference/asin-asinf-asinl.md)|Oblicza sinus łuku
[asinh, asinhf, asinhl](../c-runtime-library/reference/asinh-asinhf-asinhl.md)|Oblicza sinus hiperboliczny łuku
[atan, atanf, atanl, atan2, atan2f, atan2l](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|Oblicza tangens łuku
[atanh, atanhf, atanhl](../c-runtime-library/reference/atanh-atanhf-atanhl.md)|Oblicza tangens łuku hiperbolicznego
[_atodbl, _atodbl_l](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|Konwertuje ciąg specyficzny dla ustawień regionalnych na**`double`**
[atof, _atof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Konwertuje ciąg na**`double`**
[_atoflt, _atoflt_l, _atoldbl _atoldbl_l](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|Konwertuje ciąg specyficzny dla ustawień regionalnych na **`float`** lub**`long double`**
[cbrt, cbrtf, cbrtl](../c-runtime-library/reference/cbrt-cbrtf-cbrtl.md)|Oblicza element główny modułu
[ceil, ceilf, ceill](../c-runtime-library/reference/ceil-ceilf-ceill.md)|Oblicza granicę
[_chgsign, _chgsignf, _chgsignl](../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)|Oblicza wartość funkcji odwrotnej
[_clear87, _clearfp](../c-runtime-library/reference/clear87-clearfp.md)|Pobiera i czyści Rejestr stanu zmiennoprzecinkowego
[_control87, \_ _control87_2, _controlfp](../c-runtime-library/reference/control87-controlfp-control87-2.md)|Pobiera i ustawia słowo kontroli zmiennoprzecinkowej
[_controlfp_s](../c-runtime-library/reference/controlfp-s.md)|Bezpieczna wersja **_controlfp**
[copysign, copysignf, copysignl, _copysign, _copysignf, _copysignl](../c-runtime-library/reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)|Zwraca wartość, która ma wielkość jednego argumentu i znak innego.
[cos, cosf, cosl](../c-runtime-library/reference/cos-cosf-cosl.md)|Oblicza sinus
[cosh, coshf, coshl](../c-runtime-library/reference/cosh-coshf-coshl.md)|Oblicza sinus hiperboliczny
[DIV, ldiv, LLDiv](../c-runtime-library/reference/div.md)|Oblicza iloraz i resztę dwóch wartości całkowitych
[_ecvt](../c-runtime-library/reference/ecvt.md), [ECVT](../c-runtime-library/reference/posix-ecvt.md)|Konwertuje **`double`** do ciągu
[_ecvt_s](../c-runtime-library/reference/ecvt-s.md)|Bezpieczna wersja **_ecvt**
[ERF, erff —, erfl](../c-runtime-library/reference/erf-erff-erfl-erfc-erfcf-erfcl.md)|Oblicza funkcję błędu
[ERFC —, erfcf —, erfcl](../c-runtime-library/reference/erf-erff-erfl-erfc-erfcf-erfcl.md)|Oblicza komplementarną funkcję błędu
[exp, expf, expl](../c-runtime-library/reference/exp-expf.md)|Oblicza wykładniczą wartość *e*<sup>x</sup>
[exp2, exp2f, exp2l](../c-runtime-library/reference/exp2-exp2f-exp2l.md)|Oblicza wartość wykładniczą 2<sup>x</sup>
[expm1, expm1f, expm1l](../c-runtime-library/reference/expm1-expm1f-expm1l.md)|Obliczenia *e*<sup>x</sup>-1
[fabs, fabsf, fabsl](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|Oblicza wartość bezwzględną typu zmiennoprzecinkowego
[_fcvt](../c-runtime-library/reference/fcvt.md), [fcvt](../c-runtime-library/reference/posix-fcvt.md)|Konwertuje liczbę zmiennoprzecinkową na ciąg.
[_fcvt_s](../c-runtime-library/reference/fcvt-s.md)|Bezpieczna wersja **_fcvt**
[fdim, fdimf, fdiml](../c-runtime-library/reference/fdim-fdimf-fdiml.md)|Określa dodatnią różnicę między dwiema wartościami
[feclearexcept](../c-runtime-library/reference/feclearexcept1.md)|Czyści określone wyjątki zmiennoprzecinkowe
[fegetenv](../c-runtime-library/reference/fegetenv1.md)|Przechowuje bieżące środowisko zmiennoprzecinkowe
[fegetexceptflag](../c-runtime-library/reference/fegetexceptflag2.md)|Pobiera określony stan wyjątku zmiennoprzecinkowego
[fegetround](../c-runtime-library/reference/fegetround-fesetround2.md)|Pobiera tryb zaokrąglania zmiennoprzecinkowego
[feholdexcept](../c-runtime-library/reference/feholdexcept2.md)|Ustawia tryb wyjątku zatrzymywania zmiennoprzecinkowego
[feraiseexcept](../c-runtime-library/reference/feraiseexcept.md)|Podnosi określone wyjątki zmiennoprzecinkowe
[fesetenv](../c-runtime-library/reference/fesetenv1.md)|Ustawia bieżące środowisko zmiennoprzecinkowe
[fesetexceptflag](../c-runtime-library/reference/fesetexceptflag2.md)|Ustawia określone flagi stanu zmiennoprzecinkowego
[fesetround](../c-runtime-library/reference/fegetround-fesetround2.md)|Ustawia określony tryb zaokrąglania zmiennoprzecinkowego
[fetestexcept](../c-runtime-library/reference/fetestexcept1.md)|Określa, które flagi stanu wyjątków zmiennoprzecinkowych są ustawione
[feupdateenv](../c-runtime-library/reference/feupdateenv.md)|Przywraca środowisko zmiennoprzecinkowe, a następnie wywołuje poprzednie wyjątki
[floor, floorf, floorl](../c-runtime-library/reference/floor-floorf-floorl.md)|Oblicza piętro
[fma, fmaf, fmal](../c-runtime-library/reference/fma-fmaf-fmal.md)|Oblicza odporne na mnożenie Dodawanie
[fmax, fmaxf, fmaxl](../c-runtime-library/reference/fmax-fmaxf-fmaxl.md)|Oblicza maksymalną liczbę argumentów
[fmin, fminf, fminl](../c-runtime-library/reference/fmin-fminf-fminl.md)|Oblicza minimum argumentów
[FMOD —, fmodf —, fmodl](../c-runtime-library/reference/fmod-fmodf.md)|Oblicza pozostałą część zmiennoprzecinkową
[_fpclass, _fpclassf](../c-runtime-library/reference/fpclass-fpclassf.md)|Zwraca klasyfikację wartości zmiennoprzecinkowej.
[fpclassify](../c-runtime-library/reference/fpclassify.md)|Zwraca klasyfikację wartości zmiennoprzecinkowej.
[_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md)|Ustawia program obsługi wyjątków zmiennoprzecinkowych
[_fpreset](../c-runtime-library/reference/fpreset.md)|Resetuje środowisko zmiennoprzecinkowe
[frexp —, frexpf —, frexpl](../c-runtime-library/reference/frexp.md)|Pobiera mantysy i wykładnik liczby zmiennoprzecinkowej
[_gcvt](../c-runtime-library/reference/gcvt.md), [gcvt](../c-runtime-library/reference/posix-gcvt.md)|Konwertuje liczbę zmiennoprzecinkową na ciąg.
[_gcvt_s](../c-runtime-library/reference/gcvt-s.md)|Bezpieczna wersja **_gcvt**
[_get_FMA3_enable, _set_FMA3_enable](../c-runtime-library/reference/get-fma3-enable-set-fma3-enable.md)|Pobiera lub ustawia flagę do użycia instrukcji FMA3 na platformie x64
[hypot, hypotf, hypotl, _hypot, _hypotf, _hypotl](../c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md)|Oblicza przeciwprostokątnej
[ilogb, ilogbf, ilogbl](../c-runtime-library/reference/ilogb-ilogbf-ilogbl2.md)|Oblicza liczbę całkowitą z przedziału dziesiętnego
[imaxabs](../c-runtime-library/reference/imaxabs.md)|Oblicza wartość bezwzględną typu Integer
[imaxdiv](../c-runtime-library/reference/imaxdiv.md)|Oblicza iloraz i resztę dwóch wartości całkowitych
[isfinite, _finite, _finitef](../c-runtime-library/reference/finite-finitef.md)|Określa, czy wartość jest skończona
[isgreater, isgreaterequal, isless, islessequal, islessgreater, isunordered](../c-runtime-library/reference/floating-point-ordering.md)|Porównanie kolejności dwóch wartości zmiennoprzecinkowych
[isinf](../c-runtime-library/reference/isinf.md)|Określa, czy wartość zmiennoprzecinkowa jest nieskończona
[isnan, _isnan, _isnanf](../c-runtime-library/reference/isnan-isnan-isnanf.md)|Testuje wartość zmiennoprzecinkową dla NaN
[isnormal](../c-runtime-library/reference/isnormal.md)|Testuje, czy wartość zmiennoprzecinkowa jest ograniczona i nie była normalna
[_j0, _j1, _jn](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|Oblicza funkcję Bessela
[ldexp —, ldexpf —, ldexpl](../c-runtime-library/reference/ldexp.md)|Obliczenia x * 2<sup>n</sup>
[lgamma, lgammaf, lgammal](../c-runtime-library/reference/lgamma-lgammaf-lgammal.md)|Oblicza logarytm naturalny wartości bezwzględnej funkcji gamma
[llrint, llrintf, llrintl](../c-runtime-library/reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)|Zaokrągla wartość zmiennoprzecinkową do najbliższej wartości. **`long long`**
[llround, llroundf, llroundl](../c-runtime-library/reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md)|Zaokrągla wartość zmiennoprzecinkową do najbliższej wartości. **`long long`**
[log, logf —, logl, log10 —, log10f —, log10l](../c-runtime-library/reference/log-logf-log10-log10f.md)|Oblicza logarytm naturalny lub podstawowy-10
[log1p —, log1pf —, log1pl](../c-runtime-library/reference/log1p-log1pf-log1pl2.md)|Oblicza logarytm naturalny z 1 + x
[log2, log2f, log2l](../c-runtime-library/reference/log2-log2f-log2l.md)|Oblicza logarytm dziesiętny
[logb, logbf, logbl, _logb, _logbf](../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)|Zwraca wykładnik wartości zmiennoprzecinkowej.
[lrint, lrintf, lrintl](../c-runtime-library/reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)|Zaokrągla wartość zmiennoprzecinkową do najbliższej wartości. **`long`**
[_lrotl, _lrotr](../c-runtime-library/reference/lrotl-lrotr.md)|Obraca liczbę całkowitą w lewo lub w prawo
[lround, lroundf, lroundl](../c-runtime-library/reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md)|Zaokrągla wartość zmiennoprzecinkową do najbliższej wartości. **`long`**
[_matherr](../c-runtime-library/reference/matherr.md)|Domyślna procedura obsługi błędów matematycznych
[__max](../c-runtime-library/reference/max.md)|Makro zwracające większe dwie wartości
[__min](../c-runtime-library/reference/min.md)|Makro zwracające mniejszą liczbę dwóch wartości
[modf, modff, modfl](../c-runtime-library/reference/modf-modff-modfl.md)|Dzieli wartość zmiennoprzecinkową na części ułamkowe i całkowite.
[nan, nanf, nanl](../c-runtime-library/reference/nan-nanf-nanl.md)|Zwraca cichą wartość NaN
[nearbyint, nearbyintf, nearbyintl](../c-runtime-library/reference/nearbyint-nearbyintf-nearbyintl1.md)|Zwraca wartość zaokrągloną.
[nextafter —, nextafterf —, nextafterl, _nextafter, _nextafterf](../c-runtime-library/reference/nextafter-functions.md)|Zwraca następną reprezentację wartości zmiennoprzecinkowej
[nexttoward, nexttowardf, nexttowardl](../c-runtime-library/reference/nextafter-functions.md)|Zwraca następną reprezentację wartości zmiennoprzecinkowej
[pow, powf, powl](../c-runtime-library/reference/pow-powf-powl.md)|Zwraca wartość *x*<sup>*y*</sup>
[remainder, remainderf, remainderl](../c-runtime-library/reference/remainder-remainderf-remainderl.md)|Oblicza resztę ilorazu dwóch wartości zmiennoprzecinkowych.
[remquo, remquof, remquol](../c-runtime-library/reference/remquo-remquof-remquol.md)|Oblicza pozostałą część dwóch wartości całkowitych
[rint, rintf, rintl](../c-runtime-library/reference/rint-rintf-rintl.md)|Zaokrągla wartość zmiennoprzecinkową
[_rotl, _rotl64, _rotr, _rotr64](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|Obraca bity w typach całkowitych
[round, roundf, roundl](../c-runtime-library/reference/round-roundf-roundl.md)|Zaokrągla wartość zmiennoprzecinkową
[_scalb, _scalbf](../c-runtime-library/reference/scalb.md)|Skaluje argument z potęgą 2
[scalbn, scalbnf, scalbnl, scalbln, scalblnf, scalblnl](../c-runtime-library/reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md)|Mnoży liczbę zmiennoprzecinkową przez integralną moc **FLT_RADIX**
[_set_controlfp](../c-runtime-library/reference/set-controlfp.md)|Ustawia słowo sterujące zmiennoprzecinkowe
[_set_SSE2_enable](../c-runtime-library/reference/set-sse2-enable.md)|Włącza lub wyłącza instrukcje SSE2
[signbit](../c-runtime-library/reference/signbit.md)|Testuje bit znaku wartości zmiennoprzecinkowej
[sin, sinf, sinl](../c-runtime-library/reference/sin-sinf-sinl.md)|Oblicza sinus
[sinh, sinhf, sinhl](../c-runtime-library/reference/sinh-sinhf-sinhl.md)|Oblicza sinus hiperboliczny
[sqrt, sqrtf, sqrtl](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|Oblicza pierwiastek kwadratowy
[_status87, _statusfp, _statusfp2](../c-runtime-library/reference/status87-statusfp-statusfp2.md)|Pobiera słowo stanu zmiennoprzecinkowego
[strtof, _strtof_l](../c-runtime-library/reference/strtof-strtof-l-wcstof-wcstof-l.md)|Konwertuje ciąg na**`float`**
[strtold, _strtold_l](../c-runtime-library/reference/strtold-strtold-l-wcstold-wcstold-l.md)|Konwertuje ciąg na**`long double`**
[tan, tanf, tanl](../c-runtime-library/reference/tan-tanf-tanl.md)|Oblicza tangens
[tanh, tanhf, tanhl](../c-runtime-library/reference/tanh-tanhf-tanhl.md)|Oblicza tangens hiperboliczny
[tgamma, tgammaf, tgammal](../c-runtime-library/reference/tgamma-tgammaf-tgammal.md)|Oblicza funkcję gamma
[trunc, truncf, truncl](../c-runtime-library/reference/trunc-truncf-truncl.md)|Obcina część ułamkową
[_wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Konwertuje szeroki ciąg na**`double`**
[_y0, _y1, _yn](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|Oblicza funkcję Bessela

## <a name="see-also"></a>Zobacz także

[Procedury środowiska uruchomieniowego języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Zmiennoprzecinkowe typy pierwotne](../c-runtime-library/reference/floating-point-primitives.md)<br/>
