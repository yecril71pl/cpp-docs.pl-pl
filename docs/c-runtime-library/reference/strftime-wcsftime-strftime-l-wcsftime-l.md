---
title: strftime, wcsftime, _strftime_l, _wcsftime_l
ms.date: 03/22/2018
api_name:
- strftime
- _wcsftime_l
- _strftime_l
- wcsftime
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
ms.openlocfilehash: 0c20303973d09f48067dc331dba98a08f8f364f8
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958130"
---
# <a name="strftime-wcsftime-_strftime_l-_wcsftime_l"></a>strftime, wcsftime, _strftime_l, _wcsftime_l

Sformatuj ciąg czasu.

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

*maksymalne*<br/>
Rozmiar buforu *strDest* (**char** lub **wchar_t**).

*format*<br/>
Ciąg kontroli formatu.

*timeptr*<br/>
Struktura danych **TM** .

*ustawienie*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**strftime** zwraca liczbę znaków umieszczonych w *strDest* i **wcsftime** zwraca odpowiednią liczbę znaków dwubajtowych.

Jeśli całkowita liczba znaków, łącznie z kończącą się wartością null, jest większa *niż wartość maksymalna,* zarówno **strftime** , jak i **wcsftime** zwracają 0, a zawartość *strDest* jest nieokreślona.

Liczba znaków w *strDest* jest równa liczbie znaków literału w *formacie* , a także dowolnych znaków, które mogą być dodawane do *formatu* za pośrednictwem kodów formatowania. Zakończenie wartości null ciągu nie jest zliczane w zwracanej wartości.

## <a name="remarks"></a>Uwagi

Funkcje **strftime** i **wcsftime** formatują wartość czasu **TM** w *timeptr* zgodnie z podanym argumentem *formatu* i przechowują wynik w buforze *strDest*. Co najwyżej *, maksymalna* liczba znaków jest umieszczana w ciągu. Aby uzyskać opis pól w strukturze *timeptr* , zobacz [asctime](asctime-wasctime.md). **wcsftime** jest odpowiednikiem szerokiego znaku **strftime**; argument wskaźnika ciągu wskazuje na ciąg znaków dwubajtowych. Funkcje te zachowują się identycznie w inny sposób.

Ta funkcja sprawdza poprawność swoich parametrów. Jeśli *strDest*, *Format*lub *timeptr* jest wskaźnikiem typu null lub jeśli struktura danych **TM** zadana przez *timeptr* jest nieprawidłowa (na przykład, jeśli zawiera wartości spoza zakresu dla godziny lub daty) lub ciąg *formatu* zawiera nieprawidłowy kod formatowania, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja zwraca wartość 0 i ustawia **errno** na **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _UNICODE & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsftime**|**strftime**|**strftime**|**wcsftime**|

Argument *formatu* składa się z co najmniej jednego kodu; Podobnie jak w **printf**, kody formatowania są poprzedzone znakiem procentu ( **%** ). Znaki, które nie zaczynają **%** się od, są kopiowane niezmienione do *strDest*. Kategoria **LC_TIME** bieżących ustawień regionalnych ma wpływ na formatowanie danych wyjściowych **strftime**. (Aby uzyskać więcej informacji na temat **LC_TIME**, zobacz [setlocale](setlocale-wsetlocale.md).) Funkcje **strftime** i **wcsftime** używają obecnie ustawionych ustawień regionalnych. Wersje **_strftime_l** i **_wcsftime_l** tych funkcji są identyczne, z tą różnicą, że przyjmują ustawienia regionalne jako parametr i używają go zamiast obecnie ustawionych ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Funkcje **strftime** obsługują następujące kody formatowania:

|||
|-|-|
|Kod|Ciąg zamienny|
|**% a**|Skrócona nazwa dnia tygodnia w ustawieniach regionalnych|
|**% A**|Pełna nazwa dnia tygodnia w ustawieniach regionalnych|
|**% b**|Skrócona nazwa miesiąca w ustawieniach regionalnych|
|**% B**|Pełna nazwa miesiąca w ustawieniach regionalnych|
|**% c**|Reprezentacja daty i godziny odpowiednie dla ustawień regionalnych|
|**% C**|Rok podzielony przez 100 i obcięty do liczby całkowitej jako liczba dziesiętna (00 − 99)|
|**% d**|Dzień miesiąca jako liczba dziesiętna (01-31)|
|**% D**|Równoważne z **% m/% d/% y**|
|**% e**|Dzień miesiąca jako liczba dziesiętna (1-31), gdzie pojedyncze cyfry są poprzedzone spacją|
|**% F**|Odpowiednik do **% Y-% m-% d**|
|**% g**|Ostatnie 2 cyfry roku w formacie ISO 8601 na podstawie liczby dziesiętnej (00-99)|
|**% G**|Rok ISO 8601 na podstawie tygodnia jako liczba dziesiętna|
|**% h**|Skrócona nazwa miesiąca (odpowiednik **% b**)|
|**% H**|Godzina w formacie 24-godzinnym (00-23)|
|**% I**|Godzina w formacie 12-godzinnym (01-12)|
|**%j**|Dzień roku jako liczba dziesiętna (001-366)|
|**%m**|Miesiąc jako liczba dziesiętna (01-12)|
|**% M**|Minuta jako liczba dziesiętna (00-59)|
|**% n**|Znak nowego wiersza ( **\n**)|
|**% p**|A.M./P.M. Wskaźnik dla zegara 12-godzinnego|
|**% r**|Czas zegara 12-godzinnego dla ustawień regionalnych|
|**% R**|Równoważne z **% H:%M**|
|**% S**|Sekunda jako liczba dziesiętna (00-59)|
|**% t**|Znak tabulacji poziomej ( **\t**)|
|**%T**|Równoważne **% H:%M:% S**, format czasu ISO 8601|
|**% u**|Dzień tygodnia ISO 8601 jako liczba dziesiętna (1-7; Poniedziałek to 1)|
|**% U**|Numer tygodnia roku jako liczbę dziesiętną (00-53), gdzie pierwsza niedziela to pierwszy dzień tygodnia 1|
|**% V**|ISO 8601 numer tygodnia jako liczba dziesiętna (00-53)|
|**% w**|Dzień tygodnia jako liczba dziesiętna (0-6; Niedziela jest 0)|
|**% W**|Numer tygodnia roku jako liczbę dziesiętną (00-53), gdzie pierwszy poniedziałek to pierwszy dzień tygodnia 1|
|**% x**|Reprezentacja daty dla ustawień regionalnych|
|**% X**|Reprezentacja czasu dla ustawień regionalnych|
|**% y**|Rok bez stulecia, jako liczba dziesiętna (00-99)|
|**% Y**|Rok z stuleciem, jako liczba dziesiętna|
|**% z**|Przesunięcie od UTC w formacie ISO 8601; Brak znaków, jeśli strefa czasowa jest nieznana|
|**% Z**|Nazwa strefy czasowej lub skrót strefy czasowej, w zależności od ustawień rejestru; Brak znaków, jeśli strefa czasowa jest nieznana|
|**%%**|Znak procentu|

Podobnie jak w funkcji **printf** , **#** Flaga może mieć prefiks kodu formatowania. W takim przypadku znaczenie kodu formatu jest zmieniane w następujący sposób.

|Formatowanie kodu|Znaczenie|
|-----------------|-------------|
|**%#a**, **%#A**, **%#b**, **%#B**, **%#g**, **%#G**, **%#h**, **%#n**, **%#p**, **%#t**, **%#u**, **%#w**, **%#X**, **%#z**, **%#Z**, **%#%**|**#** Flaga jest ignorowana.|
|**% #c**|Długa reprezentacja daty i godziny, odpowiednia dla ustawień regionalnych. Przykład: "Wtorek, 14 marca 1995, 12:41:29".|
|**%#x**|Reprezentacja daty długiej, odpowiednia dla ustawień regionalnych. Przykład: "Wtorek, 14 marca 1995".|
|**% #d**, **% #D**, **% #e**, **% #F**, **% #H**, **% #I**, **% #j**, **% #m**, **%** #M, **%** **#r,% #R,% #S,% #T,% #U % #y**, **% #Y**|Usuń Wiodące zera lub spacje (jeśli istnieją).|

Tydzień w formacie ISO 8601 i rok oparty na tygodniu wyprodukowanym przez **% V**, **% g**i **% g**, używa tygodnia rozpoczynającego się w poniedziałek, gdzie tydzień 1 jest tygodniem, który zawiera czwarty tydzień, który zawiera co najmniej cztery dni roku. Jeśli pierwszy poniedziałek roku jest drugi, trzeci lub czwarty, powyższe dni są częścią ostatniego tygodnia poprzedniego roku. W tych dniach **% V** jest zastępowana przez 53, a oba **% g** i **% g** są zastępowane cyframi z poprzedniego roku.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strftime**|\<time.h>|
|**wcsftime**|\<Time. h > lub \<WCHAR. h >|
|**_strftime_l**|\<time.h>|
|**_wcsftime_l**|\<Time. h > lub \<WCHAR. h >|

Funkcje **_strftime_l** i **_wcsftime_l** są specyficzne dla firmy Microsoft. Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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
