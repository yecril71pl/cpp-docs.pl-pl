---
title: vprintf — Funkcje
ms.date: 11/04/2016
apilocation:
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- vprintf
helpviewer_keywords:
- vprintf function
- formatted text [C++]
ms.assetid: 02ac7c51-eab1-4bf0-bf4c-77065e3fa744
ms.openlocfilehash: da4f2c8586085e57925d277c452d6ed28db467d5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50573241"
---
# <a name="vprintf-functions"></a>vprintf — Funkcje

Każdy z `vprintf` funkcji pobiera wskaźnik do listy argumentów, a następnie formatuje i zapisuje dostarczone dane do określonego miejsca docelowego. Funkcje różnią się Walidacja parametru wykonywane, czy funkcje podejmują szeroki lub ciągów znaków jednobajtowych, miejsce docelowe danych wyjściowych i obsługę określania kolejności, w którym są używane parametry w ciągu formatu.

|||
|-|-|
|[_vcprintf —, _vcwprintf —](../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md)|[vfprintf —, vfwprintf —](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|
|[_vfprintf_p, _vfprintf_p_l, _vfwprintf_p, _vfwprintf_p_l](../c-runtime-library/reference/vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)|[vfprintf_s, _vfprintf_s_l, vfwprintf_s, _vfwprintf_s_l](../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)|
|[vprintf —, vwprintf —](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)|[_vprintf_p, _vprintf_p_l, _vwprintf_p, _vwprintf_p_l](../c-runtime-library/reference/vprintf-p-vprintf-p-l-vwprintf-p-vwprintf-p-l.md)|
|[vprintf_s, _vprintf_s_l, vwprintf_s, _vwprintf_s_l](../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)|[vsprintf —, vswprintf —](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)|
|[_vsprintf_p, _vsprintf_p_l, _vswprintf_p, _vswprintf_p_l](../c-runtime-library/reference/vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)|[vsprintf_s, _vsprintf_s_l, vswprintf_s, _vswprintf_s_l](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)|
|[_vscprintf, _vscprintf_l, _vscwprintf, _vscwprintf_l](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|[_vsnprintf —, _vsnwprintf —](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md)|

## <a name="remarks"></a>Uwagi

`vprintf` Funkcji są podobne do ich funkcje duplikat zgodnie z opisem w poniższej tabeli. Jednak każdy `vprintf` funkcja przyjmuje wskaźnik do listy argumentów, a każda z tych funkcji odpowiednika akceptuje listy argumentów.

Te funkcje sformatować dane wyjściowe do miejsc docelowych w następujący sposób.

|Funkcja|Odpowiednikiem — funkcja|Miejsce docelowe danych wyjściowych|Walidacja parametru|Obsługa parametr pozycyjne|
|--------------|--------------------------|------------------------|--------------------------|----------------------------------|
|`_vcprintf`|[_cprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|konsola|Sprawdź, czy wartość null.|Brak|
|`_vcwprintf`|[_cwprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|konsola|Sprawdź, czy wartość null.|Brak|
|`vfprintf`|[fprintf —](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|*Strumień*|Sprawdź, czy wartość null.|Brak|
|**vfprintf_p —**|[fprintf_p —](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|*Strumień*|Sprawdź, czy wartości null i prawidłowy format.|Tak|
|`vfprintf_s`|[fprintf_s](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|*Strumień*|Sprawdź, czy wartości null i prawidłowy format.|Brak|
|`vfwprintf`|[fwprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|*Strumień*|Sprawdź, czy wartość null.|Brak|
|**vfwprintf_p —**|[fwprintf_p —](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|*Strumień*|Sprawdź, czy wartości null i prawidłowy format.|Tak|
|`vfwprintf_s`|[fwprintf_s](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|*Strumień*|Sprawdź, czy wartości null i prawidłowy format.|Brak|
|`vprintf`|[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|`Stdout`|Sprawdź, czy wartość null.|Brak|
|**vprintf_p —**|[printf_p](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|`Stdout`|Sprawdź, czy wartości null i prawidłowy format.|Tak|
|`vprintf_s`|[printf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|`Stdout`|Sprawdź, czy wartości null i prawidłowy format.|Brak|
|`vwprintf`|[wprintf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|`Stdout`|Sprawdź, czy wartość null.|Brak|
|**vwprintf_p —**|[wprintf_p —](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|`Stdout`|Sprawdź, czy wartości null i prawidłowy format.|Tak|
|`vwprintf_s`|[wprintf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|`Stdout`|Sprawdź, czy wartości null i prawidłowy format.|Brak|
|**vsprintf**|[sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|pamięci wskazywany przez *buforu*|Sprawdź, czy wartość null.|Brak|
|**vsprintf_p —**|[sprintf_p —](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|pamięci wskazywany przez *buforu*|Sprawdź, czy wartości null i prawidłowy format.|Tak|
|`vsprintf_s`|[sprintf_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|pamięci wskazywany przez *buforu*|Sprawdź, czy wartości null i prawidłowy format.|Brak|
|`vswprintf`|[swprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|pamięci wskazywany przez *buforu*|Sprawdź, czy wartość null.|Brak|
|**vswprintf_p —**|[swprintf_p —](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|pamięci wskazywany przez *buforu*|Sprawdź, czy wartości null i prawidłowy format.|Tak|
|`vswprintf_s`|[swprintf_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|pamięci wskazywany przez *buforu*|Sprawdź, czy wartości null i prawidłowy format.|Brak|
|`_vscprintf`|[_vscprintf](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|pamięci wskazywany przez *buforu*|Sprawdź, czy wartość null.|Brak|
|`_vscwprintf`|[_vscwprintf](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|pamięci wskazywany przez *buforu*|Sprawdź, czy wartość null.|Brak|
|`_vsnprintf`|[_snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|pamięci wskazywany przez *buforu*|Sprawdź, czy wartość null.|Brak|
|`_vsnwprintf`|[_snwprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|pamięci wskazywany przez *buforu*|Sprawdź, czy wartość null.|Brak|

`argptr` Argumentów ma typ `va_list`, który jest zdefiniowany w VARARGS. H i STDARG. H. `argptr` Zmienna musi zostać zainicjowany przez **va_start** i mogą zostać zainicjowane ponownie przez kolejne `va_arg` wywołuje; `argptr` następnie wskazuje na początku listy argumentów, które są konwertowane i przesyłanych danych wyjściowych zgodnie ze specyfikacją odpowiednie w *format* argumentu. *Format* ma taką samą formę i funkcjonuje jako *format* argument [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md). Żadna z tych funkcji wywołuje `va_end`. Aby uzyskać bardziej szczegółowy opis każdego `vprintf` funkcji, zobacz opis funkcji jego odpowiednika, zgodnie z opisem w powyższej tabeli.

`_vsnprintf` różni się od **vsprintf —** , zapisuje nie więcej niż *liczba* bajtów do *buforu*.

Wersje tych funkcji **w** wrostkowe w nazwie są wersjami znaków dwubajtowych z odpowiednimi funkcjami **w** wrostkowe; w każdym z tych funkcji znaków dwubajtowych,  *Bufor* i *format* są ciągami znaków dwubajtowych. W przeciwnym wypadku każda funkcja znaków dwubajtowych działa identycznie do jego SBCS odpowiednikiem funkcji.

Wersje tych funkcji **_s** i **_p** sufiksy są bardziej bezpieczne wersje. Te wersje sprawdzanie poprawności ciągów formatu i wygeneruje wyjątek, jeśli ciąg formatu, który nie jest poprawnie sformułowany (na przykład, jeśli są używane nieprawidłowe znaki formatowania).

Wersje tych funkcji **_p** sufiks zapewniają możliwość określenia kolejność, w którym mają być zastępowane podanych argumentów w ciągu formatu. Aby uzyskać więcej informacji, zobacz [printf_p parametry pozycyjne](../c-runtime-library/printf-p-positional-parameters.md).

Aby uzyskać **vsprintf —**, `vswprintf`, `_vsnprintf` i `_vsnwprintf`, jeśli kopiowanie odbywa się między ciągów, nakładają się na siebie, zachowanie jest niezdefiniowane.

> [!IMPORTANT]
>  Upewnij się, że *format* nie jest ciągiem zdefiniowanym przez użytkownika. Aby uzyskać więcej informacji, zobacz [unikanie przepełnień bufora](/windows/desktop/SecBP/avoiding-buffer-overruns). Jeśli przy użyciu bezpieczne wersje tych funkcji (albo **_s** lub **_p** sufiksy), ciąg formatu dostarczone przez użytkownika może wywołać wyjątek nieprawidłowego parametru, jeśli zawiera ciąg dostarczone przez użytkownika nieprawidłowe znaki formatowania.

## <a name="see-also"></a>Zobacz też

[Stream operacji We/Wy](../c-runtime-library/stream-i-o.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)