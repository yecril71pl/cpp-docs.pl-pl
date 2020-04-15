---
title: strftime, wcsftime, _strftime_l, _wcsftime_l
ms.date: 4/2/2020
api_name:
- strftime
- _wcsftime_l
- _strftime_l
- wcsftime
- _o__strftime_l
- _o__wcsftime_l
- _o_strftime
- _o_wcsftime
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
ms.openlocfilehash: 5da2c128c54fd88bb874b360f5a966f17b14a935
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350015"
---
# <a name="strftime-wcsftime-_strftime_l-_wcsftime_l"></a>strftime, wcsftime, _strftime_l, _wcsftime_l

Formatowanie ciągu czasu.

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

*strDest (strDest)*<br/>
Ciąg wyjściowy.

*Maxsize*<br/>
Rozmiar bufora *strDest,* mierzony znakami **(znak** lub **wchar_t**).

*Formacie*<br/>
Ciąg kontroli formatu.

*timeptr*<br/>
struktury danych **tm.**

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**strftime** zwraca liczbę znaków umieszczonych w *strDest* i **wcsftime** zwraca odpowiednią liczbę znaków szerokich.

Jeśli całkowita liczba znaków, w tym kończące się null, jest więcej niż *maxsize,* zarówno **strftime** i **wcsftime** zwracają 0 i zawartość *strDest* są nieokreślone.

Liczba znaków w *strDest* jest równa liczbie znaków dosłownych w *formacie,* a także wszystkich znaków, które mogą być dodawane do *formatu* za pomocą kodów formatowania. Kończąca się wartość null ciągu nie jest liczona w wartości zwracanej.

## <a name="remarks"></a>Uwagi

Funkcje **strftime** i **wcsftime** formatują wartość czasu **tm** w *timepterze* zgodnie z podanym argumentem *formatu* i przechowują wynik w buforze *strDest*. Co najwyżej znaki *maxsize* są umieszczane w ciągu. Aby uzyskać opis pól w strukturze *timeptr,* zobacz [asctime](asctime-wasctime.md). **wcsftime** jest szerokim odpowiednikiem **strftime;** jego argument wskaźnika ciągu wskazuje na ciąg szerokiego znaku. Te funkcje zachowują się identycznie w przeciwnym razie.

Ta funkcja sprawdza poprawność jego parametrów. Jeśli *strDest*, *format*lub *timeptr* jest wskaźnikiem zerowym lub jeśli struktura danych **tm** adresowana przez *timeptr* jest nieprawidłowa (na przykład, jeśli zawiera wartości poza zakresem dla godziny lub daty) lub jeśli ciąg *formatu* zawiera nieprawidłowy kod formatowania, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [polu Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, funkcja zwraca 0 i ustawia **errno** na **EINVAL**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsftime**|**Strftime**|**Strftime**|**wcsftime**|

Argument *formatu* składa się z jednego lub więcej kodów; jak w **printf**, kody formatowania są**%** poprzedzone znakiem procentowym ( ). Znaki, które nie **%** zaczynają się od są kopiowane bez zmian do *strDest*. **Kategoria LC_TIME** bieżących ustawień regionalnych ma wpływ na formatowanie wyjściowe **strftime**. (Aby uzyskać więcej informacji na temat **LC_TIME,** zobacz [setlocale](setlocale-wsetlocale.md).) **Strftime** i **wcsftime** funkcje użyć aktualnie ustawione ustawienia regionalne. **_strftime_l** i **_wcsftime_l** wersje tych funkcji są identyczne, z tą różnicą, że przyjmują ustawienia regionalne jako parametr i używają tego zamiast aktualnie ustawionych ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Funkcje **strftime** obsługują te kody formatowania:

|||
|-|-|
|Code|Ciąg zastępczy|
|**%a**|Skrócona nazwa dnia tygodnia w ustawieniach regionalnych|
|**%a**|Pełna nazwa dnia tygodnia w ustawieniach regionalnych|
|**%b**|Skrócona nazwa miesiąca w ustawieniach regionalnych|
|**%b**|Pełna nazwa miesiąca w ustawieniach regionalnych|
|**%c**|Reprezentacja daty i godziny odpowiednia dla ustawień regionalnych|
|**%C**|Rok podzielony przez 100 i obcięty do liczby całkowitej, jako liczba dziesiętna (00−99)|
|**%d**|Dzień miesiąca jako liczba dziesiętna (01 - 31)|
|**%d**|Odpowiednik **%m/%d/%y**|
|**%e**|Dzień miesiąca jako liczba dziesiętna (1- 31), gdzie pojedyncze cyfry są poprzedzone spacją|
|**%f**|Odpowiednik **%Y-%m-%d**|
|**%g**|Ostatnie 2 cyfry roku tygodniowego ISO 8601 jako liczba dziesiętna (00 -99)|
|**%G**|Rok tygodniowy ISO 8601 jako liczba dziesiętna|
|**%h**|Skrócona nazwa miesiąca (odpowiednik **%b)**|
|**%H**|Godzina w formacie 24-godzinnym (00 - 23)|
|**%i**|Godzina w formacie 12-godzinnym (01 - 12)|
|**%j**|Dzień roku jako liczba dziesiętna (001 - 366)|
|**%m**|Miesiąc jako liczba dziesiętna (01 - 12)|
|**%m**|Minuta jako liczba dziesiętna (00-59)|
|**%n**|Znak nowego pliku (**\n**)|
|**%p**|Ustawienia regionalne A.M./P.M. wskaźnik dla zegara 12-godzinnego|
|**%r**|12-godzinny czas zegara ustawień regionalnych|
|**%R**|Odpowiednik **%H:%M**|
|**%s**|Drugi jako liczba dziesiętna (00 - 59)|
|**%t**|Poziomy znak zakładki (**\t**)|
|**%t**|Odpowiednik **%H:%M:%S**, format czasu ISO 8601|
|**%u**|ISO 8601 w dni powszednie jako liczba dziesiętna (1-7; Poniedziałek jest 1)|
|**%u**|Numer tygodnia roku jako liczba dziesiętna (00 - 53), gdzie pierwsza niedziela jest pierwszym dniem tygodnia 1|
|**%V**|Numer tygodnia ISO 8601 jako liczba dziesiętna (00- 53)|
|**%w**|Dzień tygodnia jako liczba dziesiętna (0 - 6; Niedziela jest 0)|
|**%W**|Numer tygodnia roku jako liczba dziesiętna (00 - 53), gdzie pierwszy poniedziałek jest pierwszym dniem tygodnia 1|
|**%x**|Reprezentacja daty dla ustawień regionalnych|
|**%X**|Reprezentacja czasu dla ustawień regionalnych|
|**%y**|Rok bez wieku, jako liczba dziesiętna (00 - 99)|
|**%Y**|Rok ze stuleciem, jako liczba dziesiętna|
|**%z**|Przesunięcie z UTC w formacie ISO 8601; brak znaków, jeśli strefa czasowa jest nieznana|
|**%Z**|Nazwa strefy czasowej ustawień regionalnych lub skrót strefy czasowej, w zależności od ustawień rejestru; brak znaków, jeśli strefa czasowa jest nieznana|
|**%%**|Znak procentowy|

Podobnie jak w funkcji **#** **printf,** flaga może prefiks dowolnego kodu formatowania. W takim przypadku znaczenie kodu formatu jest zmieniane w następujący sposób.

|Formatowanie kodu|Znaczenie|
|-----------------|-------------|
|**%#a**, **%#A**, **%#b**, **%#B**, **%#g**, **%#G**, **%#h**, **%#n**, **%#p**, **%#t**, **%#u**, **%#w**, **%#X**, **%#z**, **%#Z**,**%#%**|**#** flaga jest ignorowana.|
|**%#c**|Długa reprezentacja daty i godziny, odpowiednia dla ustawień regionalnych. Na przykład: "Wtorek, 14 marca 1995, 12:41:29".|
|**%#x**|Reprezentacja daty długiej, odpowiednia dla ustawień regionalnych. Na przykład: "Wtorek, 14 marca 1995".|
|**%#d**, **%#D**, **%#e**, **%#F**, **%#H**, **%#I**, **%#j**, **%#m**, **%#M**, **%#r**, **%#R**, **%#S**, **%#T**, **%#U**, **%#V**, **%#W**, **%#y**, **%#Y**|Usuń zera wiodące lub spacje (jeśli istnieją).|

Rok tygodniowy i tygodniowy ISO 8601 wyprodukowany przez **%V**, **%g**i **%G**używa tygodnia rozpoczynającego się w poniedziałek, gdzie tydzień 1 jest tygodniem zawierającym 4 stycznia, który jest pierwszym tygodniem obejmującym co najmniej cztery dni w roku. Jeśli pierwszy poniedziałek roku jest drugim, trzecim lub czwartym, poprzednie dni są częścią ostatniego tygodnia poprzedniego roku. W tych dniach **%V** jest zastępowany przez 53, a zarówno **%g,** jak i **%G** są zastępowane cyframi poprzedniego roku.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**Strftime**|\<> time.h|
|**wcsftime**|\<time.h> lub \<wchar.h>|
|**_strftime_l**|\<> time.h|
|**_wcsftime_l**|\<time.h> lub \<wchar.h>|

Funkcje **_strftime_l** i **_wcsftime_l** są specyficzne dla firmy Microsoft. Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [czasu](time-time32-time64.md).

## <a name="see-also"></a>Zobacz też

[Ustawienia regionalne](../../c-runtime-library/locale.md) <br/>
[Zarządzanie czasem](../../c-runtime-library/time-management.md) <br/>
[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md) <br/>
[localeconv](localeconv.md) <br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md) <br/>
[strcoll — Funkcje](../../c-runtime-library/strcoll-functions.md) <br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
