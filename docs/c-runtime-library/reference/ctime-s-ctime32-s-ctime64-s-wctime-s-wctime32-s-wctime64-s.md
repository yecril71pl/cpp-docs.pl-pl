---
title: ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s
ms.date: 4/2/2020
api_name:
- _ctime64_s
- _wctime32_s
- ctime_s
- _wctime64_s
- _ctime32_s
- _wctime_s
- _o__ctime32_s
- _o__ctime64_s
- _o__wctime32_s
- _o__wctime64_s
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ctime64_s
- _ctime32_s
- _tctime32_s
- _ctime64_s
- _wctime_s
- _tctime_s
- _tctime64_s
- ctime_s
- ctime32_s
helpviewer_keywords:
- _wctime32_s function
- ctime64_s function
- _tctime64_s function
- _wctime_s function
- tctime_s function
- _wctime64_s function
- ctime_s function
- ctime32_s function
- _ctime64_s function
- tctime64_s function
- wctime64_s function
- wctime_s function
- _tctime_s function
- tctime32_s function
- wctime32_s function
- time, converting
- _ctime32_s function
- _tctime32_s function
ms.assetid: 36ac419a-8000-4389-9fd8-d78b747a009b
ms.openlocfilehash: ca7636f7054b6c7e228b57e0e776250f1b4ccb32
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914821"
---
# <a name="ctime_s-_ctime32_s-_ctime64_s-_wctime_s-_wctime32_s-_wctime64_s"></a>ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s

Przekonwertuj wartość czasu na ciąg i Dostosuj ustawienia lokalnej strefy czasowej. Są to wersje [CTime, _ctime64 _wctime, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md) z ulepszonymi zabezpieczeniami, jak opisano w [funkcjach zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t ctime_s(
   char* buffer,
   size_t numberOfElements,
   const time_t *sourceTime
);
errno_t _ctime32_s(
   char* buffer,
   size_t numberOfElements,
   const __time32_t *sourceTime
);
errno_t _ctime64_s(
   char* buffer,
   size_t numberOfElements,
   const __time64_t *sourceTime )
;
errno_t _wctime_s(
   wchar_t* buffer,
   size_t numberOfElements,
   const time_t *sourceTime
);
errno_t _wctime32_s(
   wchar_t* buffer,
   size_t numberOfElements,
   const __time32_t *sourceTime
);
errno_t _wctime64_s(
   wchar_t* buffer,
   size_t numberOfElements,
   const __time64_t *sourceTime
);
```

```cpp
template <size_t size>
errno_t _ctime32_s(
   char (&buffer)[size],
   const __time32_t *sourceTime
); // C++ only
template <size_t size>
errno_t _ctime64_s(
   char (&buffer)[size],
   const __time64_t *sourceTime
); // C++ only
template <size_t size>
errno_t _wctime32_s(
   wchar_t (&buffer)[size],
   const __time32_t *sourceTime
); // C++ only
template <size_t size>
errno_t _wctime64_s(
   wchar_t (&buffer)[size],
   const __time64_t *sourceTime
); // C++ only
```

### <a name="parameters"></a>Parametry

*buforu*<br/>
Musi być wystarczająco duży, aby pomieścić 26 znaków. Wskaźnik do wyniku ciągu znaków lub **wartość null** , jeśli:

- *sourceTime* reprezentuje datę sprzed północy, 1 stycznia 1970, UTC.

- Jeśli używasz **_ctime32_s** lub **_wctime32_s** i *sourceTime* reprezentuje datę późniejszą niż 23:59:59 stycznia 18, 2038, UTC.

- Jeśli używasz **_ctime64_s** lub **_wctime64_s** i *sourceTime* reprezentuje datę późniejszą niż 23:59:59, 31 grudnia 3000, UTC.

- Jeśli używasz **_ctime_s** lub **_wctime_s**, te funkcje są otokami z poprzednimi funkcjami. Zobacz sekcję Uwagi.

*numberOfElements*<br/>
Rozmiar buforu.

*sourceTime*<br/>
Wskaźnik na czas przechowywania.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli powodzenie. W przypadku niepowodzenia z powodu nieprawidłowego parametru zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, zwracany jest kod błędu. Kody błędów są zdefiniowane w ERRNO. C Aby uzyskać listę tych błędów, zobacz [errno](../../c-runtime-library/errno-constants.md). W poniższej tabeli przedstawiono rzeczywiste kody błędów zgłoszone dla każdego warunku błędu.

## <a name="error-conditions"></a>Warunki błędów

|*buforu*|*numberOfElements*|*sourceTime*|Przesłać|Wartość w *buforze*|
|--------------|------------------------|------------|------------|-----------------------|
|**NULL**|ile|ile|**EINVAL**|Nie zmodyfikowano|
|Nie **ma wartości null** (wskazuje na prawidłową pamięć)|0|ile|**EINVAL**|Nie zmodyfikowano|
|Nie **ma wartości null**|0< rozmiar < 26|ile|**EINVAL**|Pusty ciąg|
|Nie **ma wartości null**|>= 26|NULL|**EINVAL**|Pusty ciąg|
|Nie **ma wartości null**|>= 26|< 0|**EINVAL**|Pusty ciąg|

## <a name="remarks"></a>Uwagi

Funkcja **ctime_s** konwertuje wartość czasu przechowywaną jako strukturę [time_t](../../c-runtime-library/standard-types.md) do ciągu znaków. Wartość *sourceTime* jest zazwyczaj uzyskiwana z wywołania [czasu](time-time32-time64.md), która zwraca liczbę sekund, które upłynęły od północy (00:00:00), 1 stycznia 1970, uniwersalny czas koordynowany (UTC). Ciąg wartości zwracanej zawiera dokładnie 26 znaków i ma postać:

`Wed Jan 02 02:03:55 1980\n\0`

Używany jest zegar 24-godzinny. Wszystkie pola mają stałą szerokość. Znak nowego wiersza ("\n") i znak null ("\ 0") zajmują ostatnie dwa pozycje ciągu.

Przekonwertowany ciąg znaków jest również dostosowywany zgodnie z ustawieniami lokalnej strefy czasowej. Zapoznaj się z funkcjami [Time](time-time32-time64.md), [_ftime](ftime-ftime32-ftime64.md)i [localtime32_s](localtime-s-localtime32-s-localtime64-s.md) , aby uzyskać informacje o konfigurowaniu czasu lokalnego i funkcji [_tzset](tzset.md) w celu uzyskania informacji na temat definiowania środowiska strefy czasowej i zmiennych globalnych.

**_wctime32_s** i **_wctime64_s** to dwubajtowa wersja **_ctime32_s** i **_ctime64_s**; Zwracanie wskaźnika do ciągu o szerokim znaku. W przeciwnym razie **_ctime64_s**, **_wctime32_s**i **_wctime64_s** zachowują się identycznie w **_ctime32_s**.

**ctime_s** to wbudowana funkcja, która oblicza **_ctime64_s** i **time_t** jest równoważna z **__time64_t**. Jeśli trzeba wymusić, aby kompilator interpretował **time_t** jako stary **time_t**32-bitowy, można zdefiniować **_USE_32BIT_TIME_T**. Spowoduje to **ctime_s** ocenę **_ctime32_s**. Nie jest to zalecane, ponieważ aplikacja może zakończyć się niepowodzeniem po 18 stycznia 2038 i nie jest dozwolona na platformach 64-bitowych.

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążenia szablonów; przeciążenia mogą automatycznie wywnioskować długość buforu, eliminując konieczność określenia argumentu rozmiaru. Aby uzyskać więcej informacji, zobacz [bezpieczne przeciążenia szablonów](../../c-runtime-library/secure-template-overloads.md).

Wersje biblioteki debugowania tych funkcji najpierw wypełniają bufor 0xFE. Aby wyłączyć to zachowanie, użyj [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _MBCS _UNICODE &|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tctime_s**|**ctime_s**|**ctime_s**|**_wctime_s**|
|**_tctime32_s**|**_ctime32_s**|**_ctime32_s**|**_wctime32_s**|
|**_tctime64_s**|**_ctime64_s**|**_ctime64_s**|**_wctime64_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**ctime_s**, **_ctime32_s**, **_ctime64_s**|\<> godziny. h|
|**_wctime_s**, **_wctime32_s**, **_wctime64_s**|\<Time. h> lub \<WCHAR. h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek uruchomieniowych języka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

```C
// crt_wctime_s.c
// This program gets the current
// time in time_t form and then uses _wctime_s to
// display the time in string form.

#include <time.h>
#include <stdio.h>

#define SIZE 26

int main( void )
{
   time_t ltime;
   wchar_t buf[SIZE];
   errno_t err;

   time( &ltime );

   err = _wctime_s( buf, SIZE, &ltime );
   if (err != 0)
   {
      printf("Invalid Arguments for _wctime_s. Error Code: %d\n", err);
   }
   wprintf_s( L"The time is %s\n", buf );
}
```

```Output
The time is Fri Apr 25 13:03:39 2003
```

## <a name="see-also"></a>Zobacz też

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
