---
title: ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64
ms.date: 11/04/2016
api_name:
- _ctime64
- _wctime32
- ctime
- _wctime64
- _ctime32
- _wctime
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
- _wctime64
- _ctime32
- _tctime
- _wctime
- _wctime32
- _tctime64
- _ctime64
- ctime
helpviewer_keywords:
- tctime64 function
- _ctime32 function
- ctime32 function
- _wctime function
- wctime64 function
- _tctime64 function
- _tctime32 function
- _ctime64 function
- _wctime64 function
- ctime function
- wctime32 function
- ctime64 function
- _wctime32 function
- _tctime function
- tctime32 function
- tctime function
- wctime function
- time, converting
ms.assetid: 2423de37-a35c-4f0a-a378-3116bc120a9d
ms.openlocfilehash: ee802e9e6ddef839f08cf6dab6573f404328b2c6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70937759"
---
# <a name="ctime-_ctime32-_ctime64-_wctime-_wctime32-_wctime64"></a>ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64

Przekonwertuj wartość czasu na ciąg i Dostosuj ustawienia lokalnej strefy czasowej. Bardziej bezpieczne wersje tych funkcji są dostępne; Zobacz [ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md).

## <a name="syntax"></a>Składnia

```C
char *ctime( const time_t *sourceTime );
char *_ctime32( const __time32_t *sourceTime );
char *_ctime64( const __time64_t *sourceTime );
wchar_t *_wctime( const time_t *sourceTime );
wchar_t *_wctime32( const __time32_t *sourceTime );
wchar_t *_wctime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>Parametry

*sourceTime*<br/>
Wskaźnik na czas przechowywania do przekonwertowania.

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do wyniku ciągu znaków. **Wartość null** zostanie zwrócona, jeśli:

- *sourceTime* reprezentuje datę sprzed północy, 1 stycznia 1970, UTC.

- Jeśli używasz **_ctime32** lub **_wctime32** i *SourceTime* reprezentuje datę po 23:59:59 stycznia 18, 2038, UTC.

- Jeśli używasz **_ctime64** lub **_wctime64** i *sourceTime* reprezentuje datę z PRZE23:59:59 grudnia, 3000, UTC.

**CTime** jest funkcją wbudowaną, która oblicza wartość **_ctime64** i **time_t** jest odpowiednikiem **__time64_t**. Jeśli trzeba wymusić, aby kompilator interpretował **time_t** jako stary 32-bitowy **time_t**, można zdefiniować **_USE_32BIT_TIME_T**. Spowoduje to **CTime** do **_ctime32**. Nie jest to zalecane, ponieważ aplikacja może zakończyć się niepowodzeniem po 18 stycznia 2038 i nie jest dozwolona na platformach 64-bitowych.

## <a name="remarks"></a>Uwagi

Funkcja **CTime** konwertuje wartość czasu przechowywaną jako wartość [time_t](../../c-runtime-library/standard-types.md) w ciągu znaków. Wartość *sourceTime* jest zazwyczaj uzyskiwana z wywołania [czasu](time-time32-time64.md), która zwraca liczbę sekund, które upłynęły od północy (00:00:00), 1 stycznia 1970, uniwersalny czas koordynowany (UTC). Ciąg wartości zwracanej zawiera dokładnie 26 znaków i ma postać:

```Output
Wed Jan 02 02:03:55 1980\n\0
```

Używany jest zegar 24-godzinny. Wszystkie pola mają stałą szerokość. Znak nowego wiersza ("\n") i znak null ("\ 0") zajmują ostatnie dwa pozycje ciągu.

Przekonwertowany ciąg znaków jest również dostosowywany zgodnie z ustawieniami lokalnej strefy czasowej. Zobacz funkcje [Time](time-time32-time64.md), [_ftime](ftime-ftime32-ftime64.md)i [localtime](localtime-localtime32-localtime64.md) , aby uzyskać informacje dotyczące konfigurowania czasu lokalnego i funkcji [_tzset](tzset.md) w celu uzyskania szczegółowych informacji na temat definiowania środowiska strefy czasowej i zmiennych globalnych.

Wywołanie **CTime** modyfikuje pojedynczy statycznie przydzielonego bufora używany przez funkcje **gmtime** i **localtime** . Każde wywołanie jednej z tych procedur niszczy wynik poprzedniego wywołania. **CTime** udostępnia bufor statyczny za pomocą funkcji **asctime** . W rezultacie wywołanie **CTime** niszczy wyniki dowolnego poprzedniego wywołania do **asctime**, **localtime**lub **gmtime**.

**_wctime** i **_wctime64** to dwubajtowa wersja **CTime** i **_ctime64**; Zwracanie wskaźnika do ciągu o szerokim znaku. W przeciwnym razie, **_ctime64**, **_wctime**i **_wctime64** zachowują się identycznie w **CTime**.

Te funkcje sprawdzają poprawność swoich parametrów. Jeśli *sourceTime* jest wskaźnikiem typu null lub jeśli wartość *sourceTime* jest ujemna, te funkcje wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcje zwracają **wartość null** i ustawiają **errno** na **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _UNICODE & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tctime**|**CTime**|**CTime**|**_wctime**|
|**_tctime32**|**_ctime32**|**_ctime32**|**_wctime32**|
|**_tctime64**|**_ctime64**|**_ctime64**|**_wctime64**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**CTime**|\<time.h>|
|**_ctime32**|\<time.h>|
|**_ctime64**|\<time.h>|
|**_wctime**|\<Time. h > lub \<WCHAR. h >|
|**_wctime32**|\<Time. h > lub \<WCHAR. h >|
|**_wctime64**|\<Time. h > lub \<WCHAR. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_ctime64.c
// compile with: /W3
/* This program gets the current
* time in _time64_t form, then uses ctime to
* display the time in string form.
*/

#include <time.h>
#include <stdio.h>

int main( void )
{
   __time64_t ltime;

   _time64( &ltime );
   printf( "The time is %s\n", _ctime64( &ltime ) ); // C4996
   // Note: _ctime64 is deprecated; consider using _ctime64_s
}
```

```Output
The time is Wed Feb 13 16:04:43 2002
```

## <a name="see-also"></a>Zobacz także

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
