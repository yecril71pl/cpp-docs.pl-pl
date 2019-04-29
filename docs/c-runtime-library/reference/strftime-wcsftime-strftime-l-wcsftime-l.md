---
title: strftime, wcsftime, _strftime_l, _wcsftime_l
ms.date: 03/22/2018
apiname:
- strftime
- _wcsftime_l
- _strftime_l
- wcsftime
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tcsftime
- strftime
- wcsftime
- _strftime_l
- _wcsftime_l
helpviewer_keywords:
- _strftime_l function
- strftime function
- tcsftime function
- _wcsftime_l function
- wcsftime function
- _tcsftime function
- time strings
ms.assetid: 6330ff20-4729-4c4a-82af-932915d893ea
ms.openlocfilehash: 932a7827ef61a5e111f86f8bc44291827843b76e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353849"
---
# <a name="strftime-wcsftime-strftimel-wcsftimel"></a>strftime, wcsftime, _strftime_l, _wcsftime_l

Format ciągu godziny.

## <a name="syntax"></a>Składnia

```C
size_t strftime(
   char *strDest,
   size_t maxsize,
   const char *format,
   const struct tm *timeptr
);
size_t _strftime_l(
   char *strDest,
   size_t maxsize,
   const char *format,
   const struct tm *timeptr,
   _locale_t locale
);
size_t wcsftime(
   wchar_t *strDest,
   size_t maxsize,
   const wchar_t *format,
   const struct tm *timeptr
);
size_t _wcsftime_l(
   wchar_t *strDest,
   size_t maxsize,
   const wchar_t *format,
   const struct tm *timeptr,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*strDest*<br/>
Ciąg wyjściowy.

*maxsize*<br/>
Rozmiar *strDest* buforu, mierzone w znakach (**char** lub **wchar_t**).

*Format*<br/>
Ciąg kontroli formatu.

*timeptr*<br/>
**TM** strukturę danych.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**strftime** zwraca liczbę znaków, umieszczone w *strDest* i **wcsftime** zwraca odpowiednią liczbę znaków dwubajtowych.

Jeśli całkowita liczba znaków, w tym kończącą wartość null, jest więcej niż *maxsize*, zarówno **strftime** i **wcsftime** zwracają 0 i zawartość  *strDest* są nieokreślone.

Liczba znaków w *strDest* jest równa liczbie znaków literałowych w *format* oraz wszystkie znaki, które mogą być dodawane do *format* za pośrednictwem kody formatowania. Zakończenia o wartości null ciągu nie jest liczony w wartości zwracanej.

## <a name="remarks"></a>Uwagi

**Strftime** i **wcsftime** funkcje formatu **tm** czasu wartość *timeptr* zgodnie z podanym  *Format* argument i magazynu wyników w buforze *strDest*. Co najwyżej *maxsize* znaki są umieszczane w ciągu. Opis pola w *timeptr* struktury, zobacz [asctime —](asctime-wasctime.md). **wcsftime** jest odpowiednikiem znaku dwubajtowego **strftime**; jej argument wskaźnika ciągu wskazuje ciąg znaków dwubajtowych. Funkcje te zachowują się identycznie.

Ta funkcja sprawdza poprawność swoich parametrów. Jeśli *strDest*, *format*, lub *timeptr* jest wskaźnikiem typu null, lub jeśli **tm** struktury danych, które zostały rozwiązane przez *timeptr* jest nieprawidłowa (na przykład, jeśli zawiera on wartości spoza zakresu dla daty lub godziny), lub jeśli *format* ciąg zawiera nieprawidłowy kod formatowania, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja zwraca 0 i ustawia **errno** do **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsftime —**|**strftime**|**strftime**|**wcsftime**|

*Format* argument składa się z co najmniej jeden kod; ponieważ w **printf**, kody formatowania są poprzedzone znakiem procentu (**%**). Znaki, które nie zaczynają się od **%** są kopiowane bez zmian do *strDest*. **LC_TIME** kategorii bieżących ustawień regionalnych, który wpływa na formatowanie danych wyjściowych z **strftime**. (Aby uzyskać więcej informacji na temat **LC_TIME**, zobacz [setlocale](setlocale-wsetlocale.md).) **Strftime** i **wcsftime** funkcje używają aktualnie ustawione ustawień regionalnych. **_Strftime_l —** i **_wcsftime_l —** wersje tych funkcji są identyczne, z tą różnicą, że pobierają ustawień regionalnych jako parametru i używać go zamiast aktualnie ustawione ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

**Strftime** funkcje obsługują te kody formatowania:

|||
|-|-|
|Kod|Ciąg zastępujący|
|**%a**|Skrót nazwy dnia tygodnia w ustawieniach regionalnych|
|**%A**|Pełna nazwa dnia tygodnia w ustawieniach regionalnych|
|**%b**|Skrócona nazwa miesiąca w ustawieniach regionalnych|
|**%B**|Pełną nazwę miesiąca w ustawieniach regionalnych|
|**%c**|Data i godzina reprezentacji odpowiednie dla ustawień regionalnych|
|**%C**|W roku podzielona przez 100 i obcięty do wartości całkowitej jako liczba dziesiętna (00−99)|
|**%d**|Dzień miesiąca jako liczbę dziesiętną (01-31)|
|**%D**|Odpowiednikiem **%m/%d/%y**|
|**%e**|Dzień miesiąca jako liczbę dziesiętną (1-31), gdzie jednej cyfry są poprzedzone spację|
|**%F**|Odpowiednikiem **%T %m -%d**|
|**%g**|Ostatnie 2 cyfr ISO 8601 oparte na tydzień roku jako liczba dziesiętna (00 - 99)|
|**%G**|ISO 8601 oparte na tydzień roku jako liczba dziesiętna|
|**%h**|Skrócona nazwa miesiąca (równoważne **%b**)|
|**%H**|Godzina w formacie 24-godzinny (00 - 23)|
|**%I**|Godzina w formacie 12-godzinny (01-12)|
|**%j**|Dzień roku jako liczba dziesiętna (001-366)|
|**%m**|Miesiąc jako liczbę dziesiętną (01-12)|
|**%M**|Minuty jako liczbę dziesiętną (00 - 59)|
|**%n**|Znak nowego wiersza (**\n**)|
|**%p**|Godzinę ustawień regionalnych. wskaźnik zegar 12-godzinny|
|**%r**|Czas zegara 12-godzinnego ustawień regionalnych|
|**%R**|Odpowiednikiem **% H: %M**|
|**%S**|Drugi jako liczba dziesiętna (00 - 59)|
|**%t**|Znak tabulacji poziomej (**\t**)|
|**%T**|Odpowiednikiem **% H: % M: %S**, format czasu ISO 8601|
|**%u**|Weekday ISO 8601 jako liczba dziesiętna (1-7; Poniedziałek to 1)|
|**%U**|Numer tygodnia roku jako liczba dziesiętna (00 - 53), gdzie pierwszej niedzieli jest pierwszy dzień tygodnia 1|
|**%V**|Numer tygodnia ISO 8601 jako liczba dziesiętna (00 - 53)|
|**%w**|Dzień tygodnia jako liczbę dziesiętną (0 – 6; Niedziela to 0)|
|**%W**|Numer tygodnia roku jako liczba dziesiętna (00 - 53), gdzie pierwszy poniedziałek jest pierwszy dzień tygodnia 1|
|**%x**|Reprezentacja daty dla ustawień regionalnych|
|**%X**|Reprezentacja czasu dla ustawień regionalnych|
|**%y**|Rok bez wieku jako liczba dziesiętna (00 - 99)|
|**%Y**|Rok, wieku, jako liczba dziesiętna|
|**%z**|Przesunięcie względem czasu UTC w formacie ISO 8601. żadne znaki, jeśli strefa czasowa jest nieznany|
|**%Z**|Ustawienia regionalne Nazwa strefy czasowej lub skrót strefy czasowej, w zależności od ustawień rejestru; żadne znaki, jeśli strefa czasowa jest nieznany|
|**%%**|Znak procentu|

Podobnie jak w **printf** funkcji **#** flagi może prefiks formatowania kodu. W takim przypadku znaczenie formatowania kodu jest zmieniany w następujący sposób.

|Formatowanie kodu|Znaczenie|
|-----------------|-------------|
|**%#a**, **%#A**, **%#b**, **%#B**, **%#g**, **%#G**, **%#h**, **%#n**, **%#p**, **%#t**, **%#u**, **%#w**, **%#X**, **%#z**, **%#Z**, **%#%**|**#** Flaga jest ignorowana.|
|**%#c**|Długi reprezentacja daty i czasu, odpowiednie dla ustawień regionalnych. Na przykład: "Wtorek, 14 marca 1995, 12:41:29".|
|**%#x**|Reprezentacja daty długiej odpowiednie dla ustawień regionalnych. Na przykład: "Wtorek, 14 marca 1995".|
|**%#d**, **%#D**, **%#e**, **%#F**, **%#H**, **% #I**, **%#j**, **%#m**, **%#M**, **%#r**, **%#R**, **%#S**, **%#T** , **%#U**, **%#V**, **%#W**, **%#y**, **%#Y**|Usuń zer wiodących ani spacji (jeśli istnieje).|

Tydzień ISO 8601 i oparte na tydzień roku produkowane przez **%V**, **%g**, i **%G**, używa tydzień, który zaczyna się w poniedziałek, gdzie 1 tydzień zawierający stycznia 4, który jest pierwszy tydzień tydzień, który zawiera co najmniej cztery dni w roku. Jeśli pierwszy poniedziałek roku jest 2, 3 lub 4, poprzednich dni są częścią ostatni tydzień roku poprzedniego. Te dni **%V** zastępuje 53, a oba **%g** i **%G** są zastępowane przez te cyfry w poprzednim roku.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strftime**|\<time.h>|
|**wcsftime**|\<Time.h > lub \<wchar.h >|
|**_strftime_l**|\<time.h>|
|**_wcsftime_l**|\<Time.h > lub \<wchar.h >|

**_Strftime_l —** i **_wcsftime_l —** funkcje są specyficzne dla firmy Microsoft. Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [czasu](time-time32-time64.md).

## <a name="see-also"></a>Zobacz także

[Wersja regionalna](../../c-runtime-library/locale.md) <br/>
[Zarządzanie czasem](../../c-runtime-library/time-management.md) <br/>
[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md) <br/>
[localeconv](localeconv.md) <br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md) <br/>
[strcoll, funkcje](../../c-runtime-library/strcoll-functions.md) <br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
