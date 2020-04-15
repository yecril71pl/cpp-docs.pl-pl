---
title: ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64
ms.date: 4/2/2020
api_name:
- _ctime64
- _wctime32
- ctime
- _wctime64
- _ctime32
- _wctime
- _o__wctime32
- _o__wctime64
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
ms.openlocfilehash: 6056ad8bac6561c0ce2902928364996b2be9ae92
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348248"
---
# <a name="ctime-_ctime32-_ctime64-_wctime-_wctime32-_wctime64"></a>ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64

Konwertuj wartość czasu na ciąg i dostosuj ustawienia lokalnej strefy czasowej. Dostępne są bezpieczniejsze wersje tych funkcji; [zobacz ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md).

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

*źródłoCzas*<br/>
Wskaźnik do przechowywanego czasu do konwersji.

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do wyniku ciągu znaku. **Wartość NULL** zostanie zwrócona, jeśli:

- *sourceTime* reprezentuje datę przed północą, 1 stycznia 1970, UTC.

- Jeśli używasz **_ctime32** lub **_wctime32** a *sourceTime* reprezentuje datę po 23:59:59 18 stycznia 2038, UTC.

- Jeśli używasz **_ctime64** lub **_wctime64** a *sourceTime* reprezentuje datę po 23:59:59, 31 grudnia 3000, UTC.

**ctime** jest funkcją wbudowaną, która ocenia **_ctime64** i **time_t** jest równoważne **__time64_t**. Jeśli konieczne jest wymuszenie, aby kompilator interpretował **time_t** jako stary **time_t**32-bitowy, można zdefiniować **_USE_32BIT_TIME_T**. W ten sposób spowoduje **ctime** do oceny **_ctime32**. Nie jest to zalecane, ponieważ aplikacja może zakończyć się niepowodzeniem po 18 stycznia 2038 r. i nie jest dozwolona na platformach 64-bitowych.

## <a name="remarks"></a>Uwagi

Funkcja **ctime** konwertuje wartość czasu przechowywaną jako wartość [time_t](../../c-runtime-library/standard-types.md) na ciąg znaków. Wartość *sourceTime* jest zwykle otrzymywana z wywołania [czasu,](time-time32-time64.md)która zwraca liczbę sekund, które upłynęło od północy (00:00:00), 1 stycznia 1970 r., skoordynowany czas uniwersalny (UTC). Ciąg wartości zwracanej zawiera dokładnie 26 znaków i ma formularz:

```Output
Wed Jan 02 02:03:55 1980\n\0
```

Używany jest zegar 24-godzinny. Wszystkie pola mają stałą szerokość. Znak nowego typu ('\n') i znak null ('\0') zajmują dwie ostatnie pozycje ciągu.

Przekonwertowany ciąg znaków jest również dostosowywany zgodnie z ustawieniami lokalnej strefy czasowej. Szczegółowe informacje na temat definiowania środowiska strefy czasowej i zmiennych globalnych można znaleźć [_tzset](tzset.md) w funkcji [czasu,](time-time32-time64.md) [_ftime](ftime-ftime32-ftime64.md)i [czasu lokalnego.](localtime-localtime32-localtime64.md)

Wywołanie **ctime** modyfikuje pojedynczy bufor statycznie przydzielone używane przez **funkcje gmtime** i **localtime.** Każde wywołanie jednej z tych procedur niszczy wynik poprzedniego wywołania. **ctime** dzieli bufor statyczny z **funkcją asctime.** Tak więc, wezwanie do **ctime** niszczy wyniki każdego poprzedniego połączenia **do asctime**, **localtime**lub **gmtime**.

**_wctime** i **_wctime64** są szerokowszą wersją **ctime** i **_ctime64;** zwracanie wskaźnika do ciągu znaków szerokoznakowych. W przeciwnym razie **_ctime64** **, _wctime**i **_wctime64** zachowywać się identycznie **jak ctime**.

Te funkcje sprawdzają ich parametry. Jeśli *sourceTime* jest wskaźnikiem null lub jeśli *sourceTime* wartość jest ujemna, te funkcje wywołać nieprawidłowy program obsługi parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, funkcje zwracają **null** i ustawić **errno** do **EINVAL**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tctime**|**Ctime**|**Ctime**|**_wctime**|
|**_tctime32**|**_ctime32**|**_ctime32**|**_wctime32**|
|**_tctime64**|**_ctime64**|**_ctime64**|**_wctime64**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**Ctime**|\<> time.h|
|**_ctime32**|\<> time.h|
|**_ctime64**|\<> time.h|
|**_wctime**|\<time.h> lub \<wchar.h>|
|**_wctime32**|\<time.h> lub \<wchar.h>|
|**_wctime64**|\<time.h> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
