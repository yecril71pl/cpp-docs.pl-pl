---
title: Standardowe typy
ms.date: 11/04/2016
f1_keywords:
- __time64_t
- _diskfree_t
- _CRT_DUMP_CLIENT
- _fsize_t
- __timeb64
- File
- __utimeb64
- jmp_buf
- __finddata64_t
- _wfinddata_t
- _finddata_t
- utimbuf64
- wint_t
- wctrans_t
- wctype_t
- _HFILE
- _secerr_handler_func
- clock_t
- fpos_t
- _dev_t
- time64_t
- wfinddata64_t
- stat64
- ldiv_t
- _EXCEPTION_POINTERS
- terminate_function
- size_t
- timeb64
- tm
- _HEAPINFO
- unexpected_function
- _CrtMemState
- _se_translator_function
- sig_atomic_t
- _CRT_REPORT_HOOK
- _complex
- _w_finddatai64_t
- _timeb
- _onexit_t
- _RTC_ErrorNumber
- lconv
- _PNH
- _off_t
- ptrdiff_t
- time_t
- _FPIEEE_RECORD
- _exception
- __w_finddata64_t
- __stat64
- _utimbuf
- __utimbuf64
- div_t
- _CRT_ALLOC_HOOK
- int8_t
- uint8_t
- int16_t
- uint16_t
- int32_t
- uint32_t
- int64_t
- int_least8_t
- uint_least8_t
- int_least16_t
- uint_least16_t
- int_least32_t
- uint_least32_t
- int_least64_t
- uint_least64_t
- int_fast8_t
- uint_fast8_t
- int_fast16_t
- uint_fast16_t
- int_fast32_t
- uint_fast32_t
- int_fast64_t
- uint_fast64_t
- intmax_t
- uintmax_t
helpviewer_keywords:
- __timeb64 type
- tm type
- clock_t type
- intptr_t type
- diskfree_t type
- wctype_t type
- CRT_DUMP_CLIENT type
- sig_atomic_t type
- _PNH type
- time_t type
- wfinddata_t type
- timeb64
- CRT, standard types
- wint_t type
- _RTC_ErrorNumber type
- _diskfree_t type
- _dev_t type
- _wfinddata_t type
- HFILE type
- __utimbuf64 type
- div_t type
- _onexit_t type
- _secerr_handler_func type
- FPIEEE_RECORD type
- HEAPINFO type
- PNH type
- _CRT_ALLOC_HOOK type
- _se_translater_function type
- va_list type
- wctrans_t type
- secerr_handler_func type
- _locale_t type
- timeb type
- lconv type
- utimbuf type
- dev_t type
- unexpected_function typedef
- _complex type
- _off_t type
- off_t type
- RTC_ErrorNumber type
- _FPIEEE_RECORD type
- exception type
- _CRT_REPORT_HOOK type
- _HEAPINFO type
- ldiv_t type
- terminate_function type
- uintptr_t type
- _CRT_DUMP_CLIENT type
- _utimbuf type
- wfinddatai64_t type
- fpos_t type
- wchar_t type
- CRT_ALLOC_HOOK type
- _HFILE type
- __time64_t type
- _timeb type
- CrtMemState type
- __finddata64_t type
- _exception type
- stat type
- onexit_t type
- FILE constant
- _stat type
- finddata_t type
- __wfinddata64_t type
- ptrdiff_t type
- complex types
- _wfinddatai64_t type
- _EXCEPTION_POINTERS type
- jmp_buf type
- se_translater_function type
- size_t type
- EXCEPTION_POINTERS type
- __stat64 type
- _fsize_t type
- CRT_REPORT_HOOK type
- _finddata_t type
ms.assetid: 23312dd2-4a6a-4d70-9b48-2a5d0d8c9f28
ms.openlocfilehash: bf90adbdbc739a2dd26d8e59ab38e56aef3bd312
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352937"
---
# <a name="standard-types"></a>Standardowe typy

Biblioteka wykonawcza firmy Microsoft definiuje następujące typy standardowe i definicje typów.

### <a name="fixed-width-integral-types-stdinth"></a>Typy całkowite o stałej szerokości (stdin. h)

|Nazwa|Równoważny typ wbudowany|
|----------|-------------------------------|
|Int8 \_ t, Uint8 \_ t|znak ze znakiem, znak bez znaku|
|Int16 \_ t, UInt16 \_ t|krótkie, niepodpisane, krótkie|
|Int32 \_ t, UInt32 \_ t|int, unsigned int|
|Int64 \_ t, UInt64 \_ t|Long Long, unsigned long long|
|int_least8_t, uint_least8_t|znak ze znakiem, znak bez znaku|
|int_least16_t, uint_least16_t|krótkie, niepodpisane, krótkie|
|int_least32_t, uint_least32_t|int, unsigned int|
|int_least64_t, uint_least64_t|Long Long, unsigned long long|
|int_fast8_t, uint_fast8_t|znak ze znakiem, znak bez znaku|
|int_fast16_t, uint_fast16_t|int, unsigned int|
|int_fast32_t, uint_fast32_t|int, unsigned int|
|int_fast64_t, uint_fast64_t|Long Long, unsigned long long|
|intmax_t, uintmax_t|Long Long, unsigned long long|

|Typ|Opis|Zadeklarowane w|
|----------|-----------------|-----------------|
|`clock_t` długo|Przechowuje wartości czasu; używany przez [zegar](../c-runtime-library/reference/clock.md).|TIME.H|
|`_complex` XML|Przechowuje rzeczywiste i urojone części liczb zespolonych; używane przez [_cabs](../c-runtime-library/reference/cabs.md).|MATH.H|
|`_CRT_ALLOC_HOOK`|Definicja typu dla zdefiniowanej przez użytkownika funkcji haka. Używane w [_CrtSetAllocHook](../c-runtime-library/reference/crtsetallochook.md).|CRTDBG.H|
|`_CRT_DUMP_CLIENT`,<br /><br /> `_CRT_DUMP_CLIENT_M`|Typ zdefiniowany dla funkcji wywołania zwrotnego, która będzie wywoływana w [_CrtMemDumpAllObjectsSince](../c-runtime-library/reference/crtmemdumpallobjectssince.md).|CRTDBG.H|
|`_CrtMemState` XML|Zawiera informacje dotyczące bieżącego stanu sterty C debugowania w czasie wykonywania.|CRTDBG.H|
|`_CRT_REPORT_HOOK`,<br /><br /> `_CRT_REPORT_HOOKW`,<br /><br /> `_CRT_REPORT_HOOKW_M`|Typ zdefiniowany dla funkcji wywołania zwrotnego, która będzie wywoływana w [_CrtDbgReport](../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md).<br /><br /> Parametry dla tej funkcji to: typ raportu, komunikat wyjściowy i wartość zwracana z funkcji wywołania zwrotnego.|CRTDBG.H|
|`dev_t`, `_dev_t` short lub unsigned Integer|Reprezentuje uchwyty urządzenia.|SYS\TYPES.H|
|`_diskfree_t` XML|Zawiera informacje o stacji dysków. Używane przez [_getdiskfree](../c-runtime-library/reference/getdiskfree.md)**.**|DOS.H i DIRECT.H|
|`div_t``ldiv_t`i `lldiv_t` struktury|Wartości są przechowywane odpowiednio przez [DIV](reference/div.md), [ldiv](../c-runtime-library/reference/ldiv-lldiv.md)i [LLDiv](../c-runtime-library/reference/ldiv-lldiv.md).|STDLIB.H|
|`errno_t` całkowitą|Używane dla zwracanego typu funkcji lub parametru, który zajmuje się kodami błędów `errno` .|STDDEF.H,<br /><br /> CRTDEFS.H|
|`_exception` XML|Przechowuje informacje o błędzie dla [_matherr](../c-runtime-library/reference/matherr.md).|MATH.H|
|`_EXCEPTION_POINTERS`|Zawiera rekord wyjątku. Aby uzyskać więcej informacji, zobacz [EXCEPTION_POINTERS](/windows/win32/api/winnt/ns-winnt-exception_pointers) .|FPIEEE.H|
|`FILE` XML|Przechowuje informacje o bieżącym stanie strumienia; używany we wszystkich operacjach we/wy strumienia.|STDIO.H|
|`_finddata_t`,,,,,,,,,, `_wfinddata_t` `_finddata32_t` `_wfinddata32_t` `_finddatai64_t` `_wfinddatai64_t` `__finddata64_t` `__wfinddata64_t` `__finddata32i64_t` `__wfinddata32i64_t` `__finddata64i32_t` , `__wfinddata64i32_t` struktury|Przechowuj informacje o atrybutach pliku zwracane przez [_findfirst, _wfindfirst i powiązane funkcje](../c-runtime-library/reference/findfirst-functions.md) oraz [_findnext, _wfindnext i powiązane funkcje](../c-runtime-library/reference/findnext-functions.md). Aby uzyskać informacje na temat elementów członkowskich struktury, zobacz [funkcje wyszukiwania nazw plików](../c-runtime-library/filename-search-functions.md) .|IO.H, WCHAR.H|
|`_FPIEEE_RECORD` XML|Zawiera informacje dotyczące wyjątku zmiennoprzecinkowego IEEE; przeszedł do procedury obsługi pułapek zdefiniowanej przez użytkownika przez [_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md).|FPIEEE.H|
|`fpos_t` (długa liczba całkowita, **`__int64`** lub struktura, w zależności od platformy docelowej)|Używane przez [fgetpos](../c-runtime-library/reference/fgetpos.md) i [fsetpos](../c-runtime-library/reference/fsetpos.md) do rejestrowania informacji do unikatowego określania każdej pozycji w pliku.|STDIO.H|
|`_fsize_t` (długa liczba całkowita bez znaku)|Używany do reprezentowania rozmiaru pliku.|IO.H,<br /><br /> WCHAR.H|
|`_HEAPINFO` XML|Zawiera informacje o następnym wpisie sterty dla [_heapwalk](../c-runtime-library/reference/heapwalk.md).|MALLOC.H|
|`_HFILE` (void \* )|Uchwyt pliku systemu operacyjnego.|CRTDBG.H|
|`imaxdiv_t`|Typ wartości zwracanej przez funkcję [imaxdiv](../c-runtime-library/reference/imaxdiv.md) , zawierający iloraz i resztę.|inttypes.h|
|`ino_t`, `_ino_t` (krótkie bez znaku)|Do zwracania informacji o stanie.|WCHAR.H|
|`intmax_t`|Typ liczby całkowitej ze znakiem może reprezentować dowolną wartość dowolnego typu liczby całkowitej ze znakiem.|stdint.h|
|`intptr_t` (Long Integer lub **`__int64`** , w zależności od platformy docelowej)|Przechowuje wskaźnik (lub UCHWYT) na platformach Win32 i Win64.|STDDEF.H i inne pliki include|
|`jmp_buf` macierzy|Używane przez [setjmp](../c-runtime-library/reference/setjmp.md) i [longjmp](../c-runtime-library/reference/longjmp.md) do zapisywania i przywracania środowiska programu.|SETJMP.H|
|`lconv` XML|Zawiera reguły formatowania dla wartości liczbowych w różnych krajach/regionach. Używany przez [localeconv](../c-runtime-library/reference/localeconv.md).|LOCALE.H|
|`_LDOUBLE`,<br /><br /> `_LONGDOUBLE`,<br /><br /> `_LDBL12` (long double lub tablica znaków bez znaku)|Służy do przedstawiania wartości typu long double.|STDLIB.H|
|`_locale_t` XML|Zapisuje bieżące wartości ustawień regionalnych; używany we wszystkich bibliotekach wykonawczych C określonych ustawień regionalnych.|CRTDEFS.H|
|`mbstate_t`|Śledzi stan konwersji znaków wielobajtowych.|WCHAR.H|
|`off_t`, `_off_t` długa liczba całkowita|Reprezentuje wartość przesunięcia pliku.|WCHAR.H, SYS\TYPES.H|
|`_onexit_t`,<br /><br /> `_onexit_m_t` przytrzymaj|Zwrócone przez [_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md).|STDLIB.H|
|`_PNH` wskaźnik do funkcji|Typ argumentu do [_set_new_handler](../c-runtime-library/reference/set-new-handler.md).|NEW.H|
|`ptrdiff_t` (Long Integer lub **`__int64`** , w zależności od platformy docelowej)|Wynik odejmowania dwóch wskaźników.|CRTDEFS.H|
|`_purecall_handler`,<br /><br /> `_purecall_handler_m`|Definicja typu dla funkcji wywołania zwrotnego, która jest wywoływana, gdy wywoływana jest czysta funkcja wirtualna. Używane przez [_get_purecall_handler, _set_purecall_handler](../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md). `_purecall_handler`Funkcja powinna mieć zwracany typ void.|STDLIB.H|
|`_RTC_error_fn` Definiuj typ|Definicja typu dla funkcji, która będzie obsługiwać kontrolę błędów czasu wykonywania. Używane w [_RTC_SetErrorFunc](../c-runtime-library/reference/rtc-seterrorfunc.md).|RTCAPI.H|
|`_RTC_error_fnW` Definiuj typ|Definicja typu dla funkcji, która będzie obsługiwać kontrolę błędów czasu wykonywania. Używane w [_RTC_SetErrorFuncW](../c-runtime-library/reference/rtc-seterrorfuncw.md).|RTCAPI.H|
|`_RTC_ErrorNumber` Licznik|Definiuje warunki błędów dla [_RTC_GetErrDesc](../c-runtime-library/reference/rtc-geterrdesc.md) i [_RTC_SetErrorType](../c-runtime-library/reference/rtc-seterrortype.md).|RTCAPI.H|
|`_se_translator_function`|Definicja typu dla funkcji wywołania zwrotnego, która tłumaczy wyjątek. Pierwszy parametr jest kodem wyjątku, a drugi parametr jest rekordem wyjątku. Używane przez [_set_se_translator](../c-runtime-library/reference/set-se-translator.md).|EH.H|
|`sig_atomic_t` całkowitą|Typ obiektu, który może być modyfikowany jako jednostka niepodzielna, nawet w obecności przerwań asynchronicznych; używany z [sygnałem](../c-runtime-library/reference/signal.md).|SIGNAL.H|
|`size_t` (niepodpisany __int64 lub liczba całkowita bez znaku, w zależności od platformy docelowej)|Wynik **`sizeof`** operatora.|CRTDEFS.H i inne pliki include|
|`_stat` XML|Zawiera informacje o stanie pliku zwrócone przez [_stat](../c-runtime-library/reference/stat-functions.md) i [_fstat](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md).|SYS\STAT.H|
|`__stat64` XML|Zawiera informacje o stanie pliku zwrócone przez [_fstat64](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md) i [_stat64](../c-runtime-library/reference/stat-functions.md)i [_wstat64](../c-runtime-library/reference/stat-functions.md).|SYS\STAT.H|
|`_stati64` XML|Zawiera informacje o stanie pliku zwrócone przez [_fstati64](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md), [_stati64](../c-runtime-library/reference/stat-functions.md)i [_wstati64](../c-runtime-library/reference/stat-functions.md).|SYS\STAT.H|
|`terminate_function` Definiuj typ|Typ definiuje się dla funkcji wywołania zwrotnego, która jest wywoływana, gdy wywoływana jest [przerwanie](../c-runtime-library/reference/terminate-crt.md) . Używane przez [set_terminate](../c-runtime-library/reference/set-terminate-crt.md).|EH.H|
|`time_t` (__int64 lub Long Integer)|Reprezentuje wartości czasu w [mktime](../c-runtime-library/reference/mktime-mktime32-mktime64.md), [Time](../c-runtime-library/reference/time-time32-time64.md), [CTime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md), [ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md), [CTime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md) i [gmtime, _gmtime32, _gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md). Liczba sekund od 1 stycznia 1970 r., 0:00 czasu UTC. Jeśli zdefiniowano _USE_32BIT_TIME_T, `time_t` jest to długa liczba całkowita. Jeśli nie jest zdefiniowana, jest to liczba całkowita 64-bitowa.|TIME.H,<br /><br /> SYS\STAT.H,<br /><br /> SYS\TIMEB.H|
|`__time32_t` (Long Integer)|Reprezentuje wartości czasu w [mktime, _mktime32, _mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md), [CTime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md), [ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md), [gmtime, _gmtime32, _gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) i [localtime, _localtime32, _localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md).|CRTDEFS.H, SYS\STAT.H,<br /><br /> SYS\TIMEB.H|
|`__time64_t` (**`__int64`**)|Reprezentuje wartości czasu w [mktime, _mktime32, _mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md), [_ctime64, _wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md), [ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md), [_gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md), [_localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md) i [_time64](../c-runtime-library/reference/time-time32-time64.md).|TIME.H,<br /><br /> SYS\STAT.H,<br /><br /> SYS\TIMEB.H|
|`_timeb` XML|Używane przez [_ftime](../c-runtime-library/reference/ftime-ftime32-ftime64.md) i [_ftime_s, _ftime32_s _ftime64_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md) do przechowywania bieżącego czasu systemowego.|SYS\TIMEB.H|
|`__timeb32` XML|Używane przez [_ftime, _ftime32, _ftime64](../c-runtime-library/reference/ftime-ftime32-ftime64.md) i [_ftime_s, _ftime32_s, _ftime64_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md) do przechowywania bieżącego czasu systemowego.|SYS\TIMEB.H|
|`__timeb64` XML|Używane przez [_ftime64](../c-runtime-library/reference/ftime-ftime32-ftime64.md) i [_ftime_s, _ftime32_s _ftime64_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md) do przechowywania bieżącego czasu systemowego.|SYS\TIMEB.H|
|`tm` XML|Używane przez [asctime, _wasctime](../c-runtime-library/reference/asctime-wasctime.md), [asctime_s, _wasctime_s](../c-runtime-library/reference/asctime-s-wasctime-s.md), [gmtime, _gmtime32, _gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md), [gmtime_s, _gmtime32_s, _gmtime64_s](../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md), [localtime, _localtime32, _localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md), [localtime_s, _localtime32_s, _localtime64_s](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md), [mktime, _mktime32, _mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md) i [strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) do przechowywania i pobierania informacji o czasie.|TIME.H|
|`uintmax_t`|Typ liczby całkowitej bez znaku może reprezentować dowolną wartość dowolnego typu liczby całkowitej bez znaku.|stdint.h|
|`uintptr_t` (Long Integer lub **`__int64`** , w zależności od platformy docelowej)|Nieoznaczona liczba całkowita bez znaku lub niepodpisana __int64 wersja `intptr_t` .|STDDEF.H i inne pliki include|
|`unexpected_function`|Typ definiuje się dla funkcji wywołania zwrotnego, która jest wywoływana, gdy wywoływana jest [nieoczekiwany](../c-runtime-library/reference/unexpected-crt.md) . Używane przez [set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md).|EH.H|
|`_utimbuf` XML|Umożliwia zapisanie czasu dostępu do pliku i modyfikacji używanych przez [_utime, _wutime](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) i [_futime _futime32, _futime64](../c-runtime-library/reference/futime-futime32-futime64.md) zmiana daty modyfikacji pliku.|SYS\UTIME.H|
|`_utimbuf32` XML|Umożliwia zapisanie czasu dostępu do pliku i modyfikacji używanych przez [_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) i [_futime](../c-runtime-library/reference/futime-futime32-futime64.md) , _futime32 _futime64 zmienić daty modyfikacji plików.|SYS\UTIME.H|
|`__utimbuf64` XML|Używane przez [_utime64, _wutime64](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) i [_futime64](../c-runtime-library/reference/futime-futime32-futime64.md) do przechowywania bieżącego czasu.|SYS\UTIME.H|
|`va_list` XML|Służy do przechowywania informacji wymaganych przez [va_arg](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) i [va_end](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) makra. Wywoływana funkcja deklaruje zmienną typu `va_list` , która może zostać przeniesiona jako argument do innej funkcji.|STDARG.H,<br /><br /> CRTDEFS.H|
|**`wchar_t`** znak dwubajtowy|Przydatne przy pisaniu przenośnych programów na rynki międzynarodowe.|STDDEF.H, STDLIB.H,<br /><br /> CRTDEFS.H,<br /><br /> SYS\STAT.H|
|`wctrans_t` całkowitą|Reprezentuje mapowania znaków specyficzne dla ustawień regionalnych.|WCTYPE.H|
|`wctype_t` całkowitą|Może reprezentować wszystkie znaki dowolnego zestawu znaków języka.|WCHAR.H,<br /><br /> CRTDEFS.H|
|`wint_t` całkowitą|Typ obiektu danych, które może mieć dowolny znak dwubajtowy lub dwubajtową wartość znaku końca pliku.|WCHAR.H,<br /><br /> CRTDEFS.H|

## <a name="see-also"></a>Zobacz też

[Dokumentacja biblioteki środowiska uruchomieniowego języka C](../c-runtime-library/c-run-time-library-reference.md)
