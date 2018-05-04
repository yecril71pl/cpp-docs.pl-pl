---
title: strftime, wcsftime, _strftime_l, _wcsftime_l | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _strftime_l function
- strftime function
- tcsftime function
- _wcsftime_l function
- wcsftime function
- _tcsftime function
- time strings
ms.assetid: 6330ff20-4729-4c4a-82af-932915d893ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 573e89b7be9818ac45f70c7c614e3bf7869c95f7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="strftime-wcsftime-strftimel-wcsftimel"></a>strftime, wcsftime, _strftime_l, _wcsftime_l

Format ciągu czasu.

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
Ciąg w danych wyjściowych.

*MaxSize*<br/>
Rozmiar *strDest* buforu, mierzony w znakach (**char** lub **wchar_t**).

*Format*<br/>
Ciąg kontroli formatu.

*timeptr*<br/>
**TM** struktury danych.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**strftime —** zwraca liczbę znaków, umieszczone w *strDest* i **wcsftime —** zwraca odpowiednia liczba znaki dwubajtowe.

Jeśli całkowita liczba znaków, w tym zakończenia wartość null, jest więcej niż *maxsize*, oba **strftime —** i **wcsftime —** zwrócić 0 i zawartość  *strDest* jest nieokreślony.

Liczba znaków w *strDest* jest równa liczbie znaków literału *format* oraz znaków, które mogą być dodawane do *format* za pośrednictwem kody formatowania. Trwa przerywanie działania null ciągu nie jest liczony w wartości zwracanej.

## <a name="remarks"></a>Uwagi

**Strftime —** i **wcsftime —** funkcji format **tm** wartości w czasie *timeptr* zgodnie z wybranych  *Format* argumentu i zapisać wynik w buforze *strDest*. Co najwyżej *maxsize* znaki są umieszczane w ciągu. Opis pól w *timeptr* struktury, zobacz [asctime —](asctime-wasctime.md). **wcsftime —** jest odpowiednikiem znaków dwubajtowych **strftime —**; jej argument ciągu wskaźnik wskazuje ciąg znaków dwubajtowych. Funkcje te działają tak samo w przeciwnym razie wartość.

Ta funkcja weryfikuje jego parametrów. Jeśli *strDest*, *format*, lub *timeptr* jest wskaźnika o wartości null, lub jeśli **tm** struktury danych dotyczy *timeptr* jest nieprawidłowy (na przykład, jeśli zawiera ona poza zakresem wartości dla daty lub godziny), lub jeśli *format* ciąg zawiera nieprawidłowy kod formatowania, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [Sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, funkcja zwraca wartość 0 i zestawy **errno** do **einval —**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsftime —**|**strftime**|**strftime**|**wcsftime**|

*Format* argument składa się z jednego lub więcej kodów; ponieważ w **printf**, formatowania kody są poprzedzone znakiem procentu (**%**). Znaki, które nie rozpoczynają się **%** zostaną skopiowane bez zmian do *strDest*. **Lc_time —** kategorii bieżące ustawienia regionalne wpływa na dane wyjściowe formatowanie **strftime —**. (Aby uzyskać więcej informacji na temat **lc_time —**, zobacz [setlocale](setlocale-wsetlocale.md).) **Strftime —** i **wcsftime —** funkcje używają aktualnie ustawione ustawień regionalnych. **_Strftime_l —** i **_wcsftime_l —** wersji te funkcje są identyczne z tą różnicą, że zająć ustawień regionalnych jako parametr i używać go zamiast aktualnie ustawione ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

**Strftime —** funkcje obsługuje te kody formatowania:

|||
|-|-|
|Kod|Ciąg zastępczy|
|**%a**|Nazwa skrócona dnia tygodnia w ustawieniach regionalnych|
|**%A**|Pełna nazwa dnia tygodnia w ustawieniach regionalnych|
|**%b**|Skrócona nazwa miesiąca w ustawieniach regionalnych|
|**%B**|Pełna nazwa miesiąca w ustawieniach regionalnych|
|**%c**|Data i godzina reprezentacji odpowiednie dla ustawień regionalnych|
|**%C**|Rok podzielona przez 100 i obcięty do liczby całkowitej jako liczbę dziesiętną (00−99)|
|**%d**|Dzień miesiąca jako liczbę dziesiętną (01-31)|
|**%D**|Odpowiednikiem **%m/%d/%y**|
|**%e**|Dzień miesiąca jako liczbę dziesiętną (1-31), gdzie pojedynczego cyfr poprzedzony spacją|
|**%F**|Odpowiednikiem **%T %m -%d**|
|**%g**|Ostatnie 2 cyfr ISO 8601 oparte na tydzień roku jako liczbę dziesiętną (00 – 99)|
|**%G**|ISO 8601 oparte na tydzień roku jako liczbę dziesiętną|
|**%h**|Skrócona nazwa miesiąca (odpowiednikiem **%b**)|
|**%H**|Godzina w formacie 24-godzinnym (00 - 23)|
|**%I**|Godzina w formacie 12-godzinnym (01-12)|
|**%j**|Dzień roku jako liczbę dziesiętną (001-366)|
|**%m**|Miesiąc jako liczbę dziesiętną (01-12)|
|**%M**|Minuta jako liczbę dziesiętną (00 - 59)|
|**%n**|Znak nowego wiersza (**\n**)|
|**%p**|Ustawienia regionalne godzinę. wskaźnik 12-godzinnym.|
|**%r**|Ustawienia regionalne 12-godzinnym zegarze|
|**%R**|Odpowiednikiem **% H: %M**|
|**%S**|Drugi jako liczbę dziesiętną (00 - 59)|
|**%t**|Znak tabulacji pozioma (**\t**)|
|**%T**|Odpowiednikiem **% H: % M: %S**, format godziny ISO 8601|
|**%u**|Dzień tygodnia ISO 8601 jako liczbę dziesiętną (1-7; Poniedziałek to 1)|
|**%U**|Numer tygodnia roku w postaci liczby dziesiętnej (00 – 53), gdzie pierwszy niedziela jest pierwszy dzień tygodnia 1|
|**%V**|Numer tygodnia ISO 8601 jako liczbę dziesiętną (00 – 53)|
|**%w**|Dzień tygodnia jako liczbę dziesiętną (0 – 6; Niedziela wynosi 0)|
|**%W**|Numer tygodnia roku w postaci liczby dziesiętnej (00 – 53), gdzie pierwszy poniedziałek jest pierwszy dzień tygodnia 1|
|**%x**|Reprezentacja daty dla ustawień regionalnych|
|**%X**|Reprezentacja czasu dla ustawień regionalnych|
|**%y**|Rok bez wieku jako liczbę dziesiętną (00 – 99)|
|**%Y**|Rok ze stuleciem jako liczbę dziesiętną|
|**%z**|Przesunięcie od czasu UTC w formacie ISO 8601. żadne znaki, jeśli strefa czasowa jest nieznany|
|**%Z**|Ustawienia regionalne Nazwa strefy czasowej albo skrót strefy czasowej, w zależności od ustawień rejestru; żadne znaki, jeśli strefa czasowa jest nieznany|
|**%%**|Znak procentu|

Podobnie jak w **printf** funkcji **#** flagi może prefiksu formatowania kodu. W takim przypadku znaczenie formatowania kodu zostanie zmieniona w następujący sposób.

|Formatowanie kodu|Znaczenie|
|-----------------|-------------|
|**% #**, **%#A**, **%#b**, **%#B**, **%#g**, **%#G**, **%#h**, **%#n**, **%#p**, **%#t**, **%#u**, **%#w**, **%#X** , **%#z**, **%#Z**, **%#%**|**#** Flaga jest ignorowana.|
|**%#c**|Long Data i godzina reprezentacji odpowiednie dla ustawień regionalnych. Na przykład: "Wtorek, marca 14, 1995 r., 12:41:29".|
|**%#x**|Reprezentacja daty długiej odpowiednich ustawień regionalnych. Na przykład: "Wtorek, 14 marca 1995".|
|**%#d**, **%#D**, **%#e**, **%#F**, **%#H**, **% #I**, **%#j**, **%#m**, **%#M**, **%#r**, **%#R**, **%#S**, **%#T** , **%#U**, **%#V**, **%#W**, **%#y**, **%#Y**|Usuń zera wiodące ani spacji (jeśli istnieje).|

ISO 8601 tygodnia oraz oparte na tydzień roku wywołanych przez **%V**, **%g**, i **%G**, używa tygodnia, który zaczyna się w poniedziałek, gdzie 1 tydzień jest zawierający stycznia 4, który jest pierwszy tydzień tydzień, która zawiera co najmniej czterech dni w roku. Jeśli pierwszy poniedziałek rok 2, 3 lub 4, poprzednich dni są częścią ostatniego tygodnia w poprzednim roku. Te dni **%V** zastępuje 53 i obu **%g** i **%G** zastępuje cyfr w poprzednim roku.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strftime**|\<time.h>|
|**wcsftime**|\<Time.h > lub \<wchar.h >|
|**_strftime_l**|\<time.h>|
|**_wcsftime_l**|\<Time.h > lub \<wchar.h >|

**_Strftime_l —** i **_wcsftime_l —** funkcje są specyficzne dla firmy Microsoft. Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [czas](time-time32-time64.md).

## <a name="see-also"></a>Zobacz także

[Wersja regionalna](../../c-runtime-library/locale.md) <br/>
[Zarządzanie czasem](../../c-runtime-library/time-management.md) <br/>
[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md) <br/>
[localeconv](localeconv.md) <br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md) <br/>
[strcoll, funkcje](../../c-runtime-library/strcoll-functions.md) <br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
