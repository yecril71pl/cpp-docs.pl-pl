---
title: _strdate_s, _wstrdate_s
ms.date: 11/04/2016
apiname:
- _strdate_s
- _wstrdate_s
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
- _strdate_s
- wstrdate_s
- _wstrdate_s
- strdate_s
- _tstrdate_s
helpviewer_keywords:
- dates, copying
- tstrdate_s function
- wstrdate_s function
- _tstrdate_s function
- strdate_s function
- copying dates
- _strdate_s function
- _wstrdate_s function
ms.assetid: d41d8ea9-e5ce-40d4-864e-1ac29b455991
ms.openlocfilehash: 85c9ab7dcad68f3aa4832236461cd38b07d4ae44
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629011"
---
# <a name="strdates-wstrdates"></a>_strdate_s, _wstrdate_s

Skopiuj bieżącą datą systemu do buforu. Są to wersje [_strdate —, _wstrdate —](strdate-wstrdate.md) ze wzmocnieniem zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t _strdate_s(
   char *buffer,
   size_t numberOfElements
);
errno_t _wstrdate_s(
   wchar_t *buffer,
   size_t numberOfElements
);
template <size_t size>
errno_t _strdate_s(
   char (&buffer)[size]
); // C++ only
template <size_t size>
errno_t _wstrdate_s(
   wchar_t (&buffer)[size]
); // C++ only
```

### <a name="parameters"></a>Parametry

*buffer*<br/>
Wskaźnik do buforu, który zostanie wprowadzona wartość ciągu daty sformatowane.

*numberOfElements*<br/>
Rozmiar buforu.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie. Wartość zwracana jest kod błędu, jeśli wystąpi awaria. Kody błędów są definiowane w numer błędu. GODZ.; Zobacz tabelę poniżej, aby dokładnie błędy generowane przez tę funkcję. Aby uzyskać więcej informacji o kodach błędów, zobacz [errno](../../c-runtime-library/errno-constants.md).

## <a name="error-conditions"></a>Warunki błędów

|*buffer*|*numberOfElements*|Wróć|Zawartość *buforu*|
|--------------|------------------------|------------|--------------------------|
|**NULL**|(wszystkie)|**EINVAL**|Nie zmodyfikowano|
|Nie **NULL** (kierujący do prawidłowego buforu)|0|**EINVAL**|Nie zmodyfikowano|
|Nie **NULL** (kierujący do prawidłowego buforu)|0 < *numberOfElements* < 9|**EINVAL**|Pusty ciąg|
|Nie **NULL** (kierujący do prawidłowego buforu)|*numberOfElements* > = 9|0|Bieżącą datę w formacie określonym w uwagi|

## <a name="security-issues"></a>Problemy dotyczące zabezpieczeń

Przekazywanie nieprawidłowy bez **NULL** wartość dla buforu spowoduje powoduje naruszenie zasad dostępu, jeśli *numberOfElements* parametr jest większe niż 9.

Przekazanie wartości rozmiarów, który jest większy niż rzeczywisty rozmiar *buforu* spowoduje przepełnienie buforu.

## <a name="remarks"></a>Uwagi

Te funkcje zapewniają bardziej bezpieczne wersje **_strdate —** i **_wstrdate —**. **_Strdate_s —** funkcja kopiuje bufor wskazywany przez bieżącą datą systemu *buforu*, sformatowany **mm**/**dd** / **rr**, gdzie **mm** to dwie cyfry reprezentującą miesiąc, **dd** to dwie cyfry reprezentującą dzień, a **RR**  to dwie ostatnie cyfry roku. Na przykład ciąg **12/05/99** reprezentuje 5 grudnia 1999. Rozmiar buforu musi zawierać co najmniej 9 znaków.

**_wstrdate_s —** to wersja znaku dwubajtowego **_strdate_s —**; argument i wartość zwracana przez **_wstrdate_s —** są ciągami znaków dwubajtowych. Funkcje te zachowują się identycznie.

Jeśli *buforu* jest **NULL** wskaźnika, lub jeśli *numberOfElements* jest mniejsza niż 9 znaków, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [ Walidacja parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają wartość -1 i ustaw **errno** do **EINVAL** Jeśli bufor jest **NULL** lub jeśli *numberOfElements*jest mniejsza niż lub równe 0 lub zestaw **errno** do **ERANGE** Jeśli *numberOfElements* jest mniejsza niż 9.

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążania szablonu; przeciążenia mogą automatycznie wywnioskować długość buforu (eliminując potrzebę określenia argumentu rozmiaru) oraz ich mogą automatycznie zastąpić starsze, niezabezpieczone funkcje ich nowsze, bezpieczne odpowiedniki. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mapping"></a>Mapowania procedur zwykłego tekstu:

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrdate_s —**|**_strdate_s**|**_strdate_s**|**_wstrdate_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_strdate**|\<time.h>|
|**_wstrdate**|\<Time.h > lub \<wchar.h >|
|**_strdate_s**|\<time.h>|

## <a name="example"></a>Przykład

Zobacz przykład [czasu](time-time32-time64.md).

## <a name="see-also"></a>Zobacz także

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
