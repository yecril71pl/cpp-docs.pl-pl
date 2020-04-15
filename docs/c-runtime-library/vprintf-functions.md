---
title: vprintf — Funkcje
ms.date: 11/04/2016
api_location:
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- vprintf
helpviewer_keywords:
- vprintf function
- formatted text [C++]
ms.assetid: 02ac7c51-eab1-4bf0-bf4c-77065e3fa744
ms.openlocfilehash: db4927e983a27110e587dacd9acf909f0c735b87
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365679"
---
# <a name="vprintf-functions"></a>vprintf — Funkcje

Każda z `vprintf` funkcji pobiera wskaźnik do listy argumentów, a następnie formatuje i zapisuje dane w określonym miejscu docelowym. Funkcje różnią się w weryfikacji parametrów wykonywane, czy funkcje mają ciągi znaków szerokich lub jedno bajtowych, miejsce docelowe danych wyjściowych i obsługi określania kolejności, w jakiej parametry są używane w ciągu formatu.

|||
|-|-|
|[_vcprintf, _vcwprintf](../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md)|[vfprintf, vfwprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|
|[_vfprintf_p, _vfprintf_p_l, _vfwprintf_p, _vfwprintf_p_l](../c-runtime-library/reference/vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)|[vfprintf_s, _vfprintf_s_l, vfwprintf_s, _vfwprintf_s_l](../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)|
|[vprintf, vwprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)|[_vprintf_p, _vprintf_p_l, _vwprintf_p, _vwprintf_p_l](../c-runtime-library/reference/vprintf-p-vprintf-p-l-vwprintf-p-vwprintf-p-l.md)|
|[vprintf_s, _vprintf_s_l, vwprintf_s, _vwprintf_s_l](../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)|[vsprintf, vswprintf](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)|
|[_vsprintf_p, _vsprintf_p_l, _vswprintf_p, _vswprintf_p_l](../c-runtime-library/reference/vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)|[vsprintf_s, _vsprintf_s_l, vswprintf_s, _vswprintf_s_l](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)|
|[_vscprintf, _vscprintf_l, _vscwprintf, _vscwprintf_l](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|[_vsnprintf, _vsnwprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md)|

## <a name="remarks"></a>Uwagi

Funkcje `vprintf` są podobne do ich funkcji odpowiednika, jak podano w poniższej tabeli. Jednak każda `vprintf` funkcja akceptuje wskaźnik do listy argumentów, podczas gdy każda z funkcji odpowiednika akceptuje listę argumentów.

Te funkcje formatowania danych dla danych wyjściowych do miejsc docelowych w następujący sposób.

|Funkcja|Odpowiednik, funkcja|Miejsce docelowe wyjścia|Sprawdzanie poprawności parametru|Obsługa parametrów pozycyjnych|
|--------------|--------------------------|------------------------|--------------------------|----------------------------------|
|`_vcprintf`|[_cprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|console|Sprawdź wartość null.|nie|
|`_vcwprintf`|[_cwprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|console|Sprawdź wartość null.|nie|
|`vfprintf`|[fprintf (druk)](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|*Strumień*|Sprawdź wartość null.|nie|
|**vfprintf_p**|[fprintf_p](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|*Strumień*|Sprawdź, czy format jest zerowy i prawidłowy.|tak|
|`vfprintf_s`|[fprintf_s](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|*Strumień*|Sprawdź, czy format jest zerowy i prawidłowy.|nie|
|`vfwprintf`|[fwprintf ( fwprintf )](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|*Strumień*|Sprawdź wartość null.|nie|
|**vfwprintf_p**|[fwprintf_p](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|*Strumień*|Sprawdź, czy format jest zerowy i prawidłowy.|tak|
|`vfwprintf_s`|[fwprintf_s](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|*Strumień*|Sprawdź, czy format jest zerowy i prawidłowy.|nie|
|`vprintf`|[Printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|`Stdout`|Sprawdź wartość null.|nie|
|**vprintf_p**|[printf_p](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|`Stdout`|Sprawdź, czy format jest zerowy i prawidłowy.|tak|
|`vprintf_s`|[Printf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|`Stdout`|Sprawdź, czy format jest zerowy i prawidłowy.|nie|
|`vwprintf`|[Wprintf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|`Stdout`|Sprawdź wartość null.|nie|
|**vwprintf_p**|[wprintf_p](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|`Stdout`|Sprawdź, czy format jest zerowy i prawidłowy.|tak|
|`vwprintf_s`|[wprintf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|`Stdout`|Sprawdź, czy format jest zerowy i prawidłowy.|nie|
|**vsprintf ( vsprintf )**|[Sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|pamięć wskazywuj *buforem*|Sprawdź wartość null.|nie|
|**vsprintf_p**|[sprintf_p](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|pamięć wskazywuj *buforem*|Sprawdź, czy format jest zerowy i prawidłowy.|tak|
|`vsprintf_s`|[sprintf_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|pamięć wskazywuj *buforem*|Sprawdź, czy format jest zerowy i prawidłowy.|nie|
|`vswprintf`|[swprintf ( swprintf )](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|pamięć wskazywuj *buforem*|Sprawdź wartość null.|nie|
|**vswprintf_p**|[swprintf_p](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|pamięć wskazywuj *buforem*|Sprawdź, czy format jest zerowy i prawidłowy.|tak|
|`vswprintf_s`|[swprintf_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|pamięć wskazywuj *buforem*|Sprawdź, czy format jest zerowy i prawidłowy.|nie|
|`_vscprintf`|[_vscprintf](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|pamięć wskazywuj *buforem*|Sprawdź wartość null.|nie|
|`_vscwprintf`|[_vscwprintf](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|pamięć wskazywuj *buforem*|Sprawdź wartość null.|nie|
|`_vsnprintf`|[_snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|pamięć wskazywuj *buforem*|Sprawdź wartość null.|nie|
|`_vsnwprintf`|[_snwprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|pamięć wskazywuj *buforem*|Sprawdź wartość null.|nie|

Argument `argptr` ma `va_list`typ , który jest zdefiniowany w VARARGS. H i STDARG. H. Zmienna `argptr` musi być zainicjowana przez **va_start** i może zostać ponownie `va_arg` zainicjowana przez kolejne wywołania; `argptr` następnie wskazuje na początek listy argumentów, które są konwertowane i przekazywane do danych wyjściowych zgodnie z odpowiednimi specyfikacjami w argumentie *formatu.* *format* ma taką samą formę i funkcję jak argument *formatu* [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md). Żadna z tych `va_end`funkcji nie wywołuje . Aby uzyskać pełniejszy opis każdej `vprintf` funkcji, zobacz opis funkcji jego odpowiednika, jak wymieniono w powyższej tabeli.

`_vsnprintf`różni się od **vsprintf** tym, że zapisuje nie więcej niż *liczbę* bajtów do *bufora*.

Wersje tych funkcji z **infix w** nazwie są wersjami szerokoznakowymi odpowiednich funkcji bez **w** infix; w każdej z tych funkcji szerokich znaków *bufor* i *format* są ciągami znaków szerokich. W przeciwnym razie każda funkcja szerokich znaków zachowuje się identycznie jak jego funkcja odpowiednika SBCS.

Wersje tych funkcji z **_s** i **_p** sufiksami są bardziej bezpieczne wersje. Te wersje sprawdzają poprawność ciągów formatu i wygenerują wyjątek, jeśli ciąg formatu nie jest dobrze sformułowany (na przykład, jeśli używane są nieprawidłowe znaki formatowania).

Wersje tych funkcji z sufiksem **_p** umożliwiają określenie kolejności, w jakiej podane argumenty są podstawione w ciągu formatu. Aby uzyskać więcej informacji, zobacz [printf_p Parametry pozycyjne](../c-runtime-library/printf-p-positional-parameters.md).

W przypadku **vsprintf**, `vswprintf` `_vsnprintf` i `_vsnwprintf`, jeśli kopiowanie występuje między ciągami, które nakładają się, zachowanie jest niezdefiniowane.

> [!IMPORTANT]
> Upewnij się, że *format* nie jest ciągiem zdefiniowanym przez użytkownika. Aby uzyskać więcej informacji, zobacz [Unikanie przekroczenia buforu](/windows/win32/SecBP/avoiding-buffer-overruns). W przypadku korzystania z bezpiecznych wersji tych funkcji **(_s** lub **_p** sufiksów), ciąg formatu dostarczony przez użytkownika może wyzwolić nieprawidłowy wyjątek parametru, jeśli ciąg dostarczony przez użytkownika zawiera nieprawidłowe znaki formatowania.

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../c-runtime-library/stream-i-o.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)
