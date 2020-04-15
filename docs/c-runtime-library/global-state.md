---
title: Stan globalny w CRT
ms.date: 04/02/2020
helpviewer_keywords:
- CRT global state
ms.openlocfilehash: 487418da104b2edbc45b5d3a664e4385394ada31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81379101"
---
# <a name="global-state-in-the-crt"></a>Stan globalny w CRT

Niektóre funkcje w uniwersalnym czasie wykonywania C (UCRT) używają stanu globalnego. Na przykład `setlocale()` ustawia ustawienia regionalne dla całego programu, co wpływa na separatory cyfr, tekstową stronę kodową itd.

Stan globalny UCRT nie jest współużytkowane przez aplikacje i system operacyjny. Na przykład jeśli aplikacja `setlocale()`wywołuje , nie będzie miało wpływu na ustawienia regionalne dla wszystkich składników systemu operacyjnego, który używa czasu wykonywania C lub odwrotnie.

## <a name="os-specific-versions-of-crt-functions"></a>Specyficzne dla systemu operacyjnego wersje funkcji CRT

W UCRT funkcje, które współdziałają ze stanem globalnym `_o_`mają funkcję "bliźniaczą", poprzedzone . Przykład:

    `setlocale()` affects global state specific to the app.
    `_o_setlocale()` affects global state shared by all OS components, but not apps.

Jedyną różnicą między tymi funkcjami "bliźniaczych" jest to, że podczas odczytu/zapisu globalnego stanu `_o_`CRT wersje specyficzne dla systemu operacyjnego (czyli wersje, które zaczynają się od) używają kopii systemu operacyjnego stanu globalnego zamiast kopii aplikacji stanu globalnego.

Wersje tych funkcji specyficzne dla systemu `ucrt.osmode.lib`operacyjnego znajdują się w pliku . Na przykład wersja specyficzne dla `setlocale()` systemu operacyjnego jest`_o_setlocale()`

Istnieją dwa sposoby izolowania stanu CRT składnika od stanu CRT aplikacji:

- Statycznie połączyć składnik przy użyciu opcji kompilatora /MT (release) lub MTd (debug). Aby uzyskać szczegółowe informacje, zobacz [/MD, /MT, /LD](https://docs.microsoft.com/cpp/build/reference/md-mt-ld-use-run-time-library?view=vs-2019). Należy zauważyć, że łączenie statyczne może znacznie zwiększyć rozmiar binarny.
- Począwszy od systemu Windows 10 20H2, uzyskać izolację stanu CRT dynamicznie łącząc się z CRT, ale wywołać eksport w trybie systemu operacyjnego (funkcje, które zaczynają się _od o_). Aby wywołać eksport w trybie systemu operacyjnego, statycznie łącze jak `/NODEFAULTLIB:libucrt.lib` poprzednio, `/NODEFAULTLIB:libucrtd.lib` ale ignoruj statyczne UCRT za pomocą opcji konsolidatora (release) lub (debug) Zobacz [/NODEFAULTLIB (Ignoruj biblioteki)](https://docs.microsoft.com/cpp/build/reference/nodefaultlib-ignore-libraries?view=vs-2019) aby uzyskać szczegółowe informacje. I `ucrt.osmode.lib` dodać do wejścia konsolidatora.

> [!Note]
> W kodzie `setlocale()`źródłowym `_o_setlocale()`napisz , nie . Po połączeniu `ucrt.osmode.lib`z programem konsolidator automatycznie zastąpi wersję funkcji specyficzną dla systemu operacyjnego. Oznacza to, `setlocale()` że zostaną `_o_setlocale()`zastąpione .

Łączenie przeciwko `ucrt.osmode.lib` wyłącza niektóre wywołania UCRT, które są dostępne tylko w trybie aplikacji. Próba wywołania tych spowoduje błąd łącza.

## <a name="global-state-affected-by-appos-separation"></a>Globalny stan, na który ma wpływ separacja między aplikacjami/systemami operacyjnymi

Stan globalny, na który ma wpływ oddzielenie aplikacji i stanu systemu operacyjnego, obejmuje:

- [Dane ustawień regionalnych](locale.md)
- Obsługa sygnału ustawiona przez [sygnał](reference/signal.md)
- Procedury zakończenia ustawione przez [zakończenie](reference/set-terminate-crt.md)
- [errno i _doserrno](errno-doserrno-sys-errlist-and-sys-nerr.md)
- Stan generowania liczb losowych używany przez [rand](reference/rand.md) i [srand](reference/srand.md)
- Funkcje, które zwracają bufor, którego użytkownik nie musi zwolnić: [strtok, wcstok, _mbstok](reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) [Tmpnam, _wtmpnam](reference/tempnam-wtempnam-tmpnam-wtmpnam.md) [asctime, _wasctime](reference/asctime-wasctime.md) [gmtime, _gmtime32, _gmtime64](reference/gmtime-gmtime32-gmtime64.md) [_fcvt](reference/fcvt.md) [_ecvt](reference/ecvt.md) [strerror, _strerror, _wcserror, __wcserror](reference/strerror-strerror-wcserror-wcserror.md)
- Bufor używany przez [_putch, _putwch](reference/putch-putwch.md)
- [_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)
- [_set_new_handler](reference/set-new-handler.md) i [_set_new_mode](reference/set-new-mode.md)
- [fmode] (text-and-binary-mode-file-i-o.md)
- [Informacje o strefie czasowej](time-management.md)

## <a name="see-also"></a>Zobacz też

[C Odwołanie do biblioteki czasu wykonywania](c-run-time-library-reference.md)