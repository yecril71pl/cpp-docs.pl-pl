---
title: asctime_s, _wasctime_s
ms.date: 4/2/2020
api_name:
- _wasctime_s
- asctime_s
- _o__wasctime_s
- _o_asctime_s
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
- api-ms-win-crt-time-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- asctime_s
- _wasctime_s
- _tasctime_s
helpviewer_keywords:
- tasctime_s function
- _tasctime_s function
- time structure conversion
- wasctime_s function
- time, converting
- _wasctime_s function
- asctime_s function
ms.assetid: 17ad9b2b-a459-465d-976a-42822897688a
ms.openlocfilehash: 52391eb1237e4c1d7ef320dacd211b603a21ab8b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81334226"
---
# <a name="asctime_s-_wasctime_s"></a>asctime_s, _wasctime_s

Konwertowanie struktury czasu **tm** na ciąg znaków. Te funkcje są wersjami [asctime, _wasctime](asctime-wasctime.md) z ulepszeniami zabezpieczeń, jak opisano w [funkcji zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t asctime_s(
   char* buffer,
   size_t numberOfElements,
   const struct tm *tmSource
);
errno_t _wasctime_s(
   wchar_t* buffer,
   size_t numberOfElements
   const struct tm *tmSource
);
template <size_t size>
errno_t asctime_s(
   char (&buffer)[size],
   const struct tm *tmSource
); // C++ only
template <size_t size>
errno_t _wasctime_s(
   wchar_t (&buffer)[size],
   const struct tm *tmSource
); // C++ only
```

### <a name="parameters"></a>Parametry

*Buforu*<br/>
Wskaźnik do buforu do przechowywania wyniku ciągu znaków. Ta funkcja przyjmuje wskaźnik do prawidłowej lokalizacji pamięci o rozmiarze określonym przez *numberOfElements*.

*liczbaOfElements*<br/>
Rozmiar buforu używanego do przechowywania wyniku.

*źródło tmSource*<br/>
Struktura czasu/daty. Ta funkcja przyjmuje wskaźnik do prawidłowego **obiektu tm struktury.** **tm**

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli się powiedzie. Jeśli wystąpi błąd, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w programie [Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, wartość zwracana jest kodem błędu. Kody błędów są zdefiniowane w ERRNO. H. Aby uzyskać więcej informacji, zobacz [errno Constants](../../c-runtime-library/errno-constants.md). Rzeczywiste kody błędów zwrócone dla każdego warunku błędu są wyświetlane w poniższej tabeli.

### <a name="error-conditions"></a>Warunki błędu

|*Buforu*|*liczbaOfElements*|*źródło tmSource*|Zwraca|Wartość w *buforze*|
|--------------|------------------------|----------|------------|-----------------------|
|**Null**|Dowolne|Dowolne|**Einval**|Nie zmodyfikowano|
|Nie **NULL** (punkty do prawidłowej pamięci)|0|Dowolne|**Einval**|Nie zmodyfikowano|
|Nie **NULL**|0< rozmiar < 26|Dowolne|**Einval**|Pusty ciąg znaków|
|Nie **NULL**|>= 26|**Null**|**Einval**|Pusty ciąg znaków|
|Nie **NULL**|>= 26|Nieprawidłowa struktura czasu lub wartości poza zakresem dla składników czasu|**Einval**|Pusty ciąg znaków|

> [!NOTE]
> Warunki błędu dla **wasctime_s** są podobne do **asctime_s** z wyjątkiem tego, że limit rozmiaru jest mierzony w słowach.

## <a name="remarks"></a>Uwagi

Funkcja **asctime** konwertuje czas przechowywany jako struktura na ciąg znaków. Wartość *tmSource* jest zwykle uzyskiwana z wywołania **do gmtime** lub **localtime**. Obie funkcje mogą być używane do wypełniania struktury **tm,** zgodnie z definicją w time. H.

|Element członkowski timeptr|Wartość|
|--------------------|-----------|
|**tm_hour**|Godziny od północy (0-23)|
|**tm_isdst**|Dodatnie, jeśli obowiązuje czas letni; 0, jeśli czas letni nie obowiązuje; ujemny, jeśli stan czasu letniego jest nieznany. Biblioteka wykonawcza języka C przyjmuje reguły Stanów Zjednoczonych dotyczące implementowania obliczania czasu letniego (DST).|
|**tm_mday**|Dzień miesiąca (1-31)|
|**tm_min**|Minuty po godzinie (0-59)|
|**tm_mon**|Miesiąc (0-11; Styczeń = 0)|
|**tm_sec**|Sekundy po minucie (0-59)|
|**tm_wday**|Dzień tygodnia (0-6; Niedziela = 0)|
|**tm_yday**|Dzień roku (0-365; 1 stycznia = 0)|
|**tm_year**|Rok (rok bieżący minus 1900)|

Przekonwertowany ciąg znaków jest również dostosowywany zgodnie z ustawieniami lokalnej strefy czasowej. Aby uzyskać informacje na temat definiowania środowiska strefy czasowej i zmiennych globalnych, zobacz [funkcje time, _time32, _time64](time-time32-time64.md) [, _ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)i [localtime_s, _localtime32_s _localtime64_s](localtime-s-localtime32-s-localtime64-s.md) informacje dotyczące konfigurowania czasu lokalnego i funkcji [_tzset.](tzset.md)

Wynik ciągu wyprodukowany przez **asctime_s** zawiera dokładnie 26 znaków `Wed Jan 02 02:03:55 1980\n\0`i ma formularz . Używany jest zegar 24-godzinny. Wszystkie pola mają stałą szerokość. Nowy znak wiersza i znak null zajmują dwie ostatnie pozycje ciągu. Wartość przekazana jako drugi parametr powinna być co najmniej tak duża. Jeśli jest mniejsza, zostanie zwrócony kod błędu **EINVAL.**

**_wasctime_s** jest szerokoznakową wersją **asctime_s**. **_wasctime_s** i **asctime_s** zachowują się identycznie w przeciwnym razie.

Wersje biblioteki debugowania tych funkcji najpierw wypełniają bufor 0xFE. Aby wyłączyć to zachowanie, użyj [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mapping"></a>Mapowanie rutynowych tekstu ogólnego

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tasctime_s**|**asctime_s**|**asctime_s**|**_wasctime_s**|

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążenia szablonu; przeciążenia można wywnioskować długość buforu automatycznie, eliminując konieczność określenia argumentu rozmiaru. Aby uzyskać więcej informacji, zobacz [Bezpieczne przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**asctime_s**|\<> time.h|
|**_wasctime_s**|\<time.h> lub \<wchar.h>|

## <a name="security"></a>Zabezpieczenia

Jeśli wskaźnik buforu nie jest **null** i wskaźnik nie wskazuje prawidłowego buforu, funkcja zastąpi cokolwiek jest w lokalizacji. Może to również spowodować naruszenie zasad dostępu.

[Przepełnienie buforu](/windows/win32/SecBP/avoiding-buffer-overruns) może wystąpić, jeśli argument size przekazany jest większy niż rzeczywisty rozmiar buforu.

## <a name="example"></a>Przykład

Ten program umieszcza czas systemowy w długim **całkowitym blokadie,** przekłada go na **newtime** struktury, a następnie konwertuje go do postaci ciągu dla danych wyjściowych, przy użyciu funkcji **asctime_s.**

```C
// crt_asctime_s.c
#include <time.h>
#include <stdio.h>

struct tm newtime;
__time32_t aclock;

int main( void )
{
   char buffer[32];
   errno_t errNum;
   _time32( &aclock );   // Get time in seconds.
   _localtime32_s( &newtime, &aclock );   // Convert time to struct tm form.

   // Print local time as a string.

   errNum = asctime_s(buffer, 32, &newtime);
   if (errNum)
   {
       printf("Error code: %d", (int)errNum);
       return 1;
   }
   printf( "Current date and time: %s", buffer );
   return 0;
}
```

```Output
Current date and time: Wed May 14 15:30:17 2003
```

## <a name="see-also"></a>Zobacz też

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
