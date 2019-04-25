---
title: ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64
ms.date: 11/04/2016
apiname:
- _ctime64
- _wctime32
- ctime
- _wctime64
- _ctime32
- _wctime
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
ms.openlocfilehash: d1858a36c68a2ca5cedf70a1d74d5f250cbac8df
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62288606"
---
# <a name="ctime-ctime32-ctime64-wctime-wctime32-wctime64"></a>ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64

Konwertuj na wartość godziny na ciąg, a następnie dostosować ustawienia strefy czasu lokalnego. Bardziej bezpieczne wersje tych funkcji są dostępne; zobacz [ctime_s, _ctime32_s, _ctime64_s —, _wctime_s —, _wctime32_s, _wctime64_s —](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md).

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

Wskaźnik wynikowy ciąg znaków. **Wartość NULL** zostanie zwrócona, jeśli:

- *sourceTime* reprezentuje datę wcześniejszą o północy, 1 stycznia 1970 r., czasu UTC.

- Jeśli używasz **_ctime32 —** lub **_wctime32 —** i *sourceTime* reprezentuje datę wypadającą po 23:59:59 18 stycznia 2038 r. UTC.

- Jeśli używasz **_ctime64** lub **_wctime64** i *sourceTime* reprezentuje datę wypadającą po 23:59:59, 31 grudnia 3000, czasu UTC.

**ctime** jest funkcją śródwierszową, co jest ewaluowane jako **_ctime64** i **time_t** jest odpowiednikiem **__time64_t —**. Jeśli chcesz wymusić na kompilatorze interpretowanie **time_t** jako stary 32-bitowy **time_t**, można zdefiniować **_USE_32BIT_TIME_T**. Takie działanie spowoduje **ctime** na **_ctime32 —**. Nie jest to zalecane, ponieważ aplikacja może przestać działać po 18 stycznia 2038 r. i nie jest dozwolone na platformach 64-bitowych.

## <a name="remarks"></a>Uwagi

**Ctime** funkcja konwertuje wartość czasu, przechowywane jako [time_t](../../c-runtime-library/standard-types.md) wartość na ciąg znaków. *SourceTime* wartość zwykle jest uzyskiwana w wyniku wywołania [czasu](time-time32-time64.md), która zwraca liczbę sekund, które upłynęły od północy (00: 00:00), 1 stycznia 1970 r., skoordynowanego czasu uniwersalnego (UTC). Ciągu wartość zwracana zawiera dokładnie 26 znaków i ma postać:

```Output
Wed Jan 02 02:03:55 1980\n\0
```

Używany jest zegar 24-godzinny. Wszystkie pola są stałej szerokości. Znak nowego wiersza (\n) i znak null (\0) zajmują się dwie ostatnie pozycje ciągu.

Ciąg przekonwertowany znak również jest dostosowywany zgodnie z ustawieniami strefy czasu lokalnego. Zobacz [czasu](time-time32-time64.md), [_ftime](ftime-ftime32-ftime64.md), i [localtime](localtime-localtime32-localtime64.md) funkcji, aby uzyskać informacje na temat konfigurowania lokalnego czasu i [_tzset —](tzset.md) działać w ramach szczegółowe informacje na temat definiowania środowiska strefy czasowej i zmienne globalne.

Wywołanie **ctime** modyfikuje pojedynczego buforu statycznie przydzielanego posługują się **gmtime** i **localtime** funkcji. Każde wywołanie jednej z tych procedur niszczy wynik poprzedniego wywołania. **ctime** udostępnia statyczny bufor o **asctime —** funkcji. W związku z tym, wywołanie **ctime** niszczy wyniki każdego poprzedniego wywołania do **asctime —**, **localtime**, lub **gmtime**.

**_wctime** i **_wctime64** to wersja znaku dwubajtowego **ctime** i **_ctime64**; zwracającej wskaźnik do ciągu znaków dwubajtowych. W przeciwnym razie **_ctime64**, **_wctime**, i **_wctime64** zachowują się identycznie do **ctime**.

Te funkcje sprawdzają poprawność swoich parametrów. Jeśli *sourceTime* jest wskaźnikiem typu null, lub jeśli *sourceTime* wartość jest ujemna, te funkcje wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają **NULL** i ustaw **errno** do **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tctime —**|**ctime —**|**ctime —**|**_wctime**|
|**_tctime32**|**_ctime32**|**_ctime32**|**_wctime32**|
|**_tctime64 —**|**_ctime64**|**_ctime64**|**_wctime64**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**ctime —**|\<time.h>|
|**_ctime32**|\<time.h>|
|**_ctime64**|\<time.h>|
|**_wctime**|\<Time.h > lub \<wchar.h >|
|**_wctime32**|\<Time.h > lub \<wchar.h >|
|**_wctime64**|\<Time.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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
