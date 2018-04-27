---
title: ctime_s —, _ctime32_s —, _ctime64_s —, _wctime_s —, _wctime32_s —, _wctime64_s — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _ctime64_s
- _wctime32_s
- ctime_s
- _wctime64_s
- _ctime32_s
- _wctime_s
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
- ctime64_s
- _ctime32_s
- _tctime32_s
- _ctime64_s
- _wctime_s
- _tctime_s
- _tctime64_s
- ctime_s
- ctime32_s
dev_langs:
- C++
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
caps.latest.revision: 27
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9d598ab0ef9aa2509e68e768182568870eb85e5d
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="ctimes-ctime32s-ctime64s-wctimes-wctime32s-wctime64s"></a>ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s

Wartość czasu jest skonwertowana do ciągu oraz dostosować ustawienia strefy czasu lokalnego. Są to wersje [ctime —, _ctime64 —, _wctime —, _wctime64 —](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*buffer*<br/>
Musi być wystarczająco duży, aby pomieścić 26 znaków. Wskaźnik do wyniku ciąg znaków lub **NULL** jeśli:

- *sourceTime* reprezentuje datę przed północy, 1 stycznia 1970 UTC.

- Jeśli używasz **_ctime32_s —** lub **_wctime32_s —** i *sourceTime* reprezentuje datę wypadającą po 23:59:59 18 stycznia 2038 r., UTC.

- Jeśli używasz **_ctime64_s —** lub **_wctime64_s —** i *sourceTime* reprezentuje datę wypadającą po 23:59:59 31 grudnia 3000 UTC.

- Jeśli używasz **_ctime_s** lub **_wctime_s —**, te funkcje są otoki do poprzedniej funkcji. W sekcji uwag.

*numberOfElements*<br/>
Rozmiar buforu.

*sourceTime*<br/>
Wskaźnik do czasu przechowywane.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie. W przypadku awarii z powodu nieprawidłowego parametru, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, zostanie zwrócony kod błędu. Kody błędów są definiowane w numer błędu. H; Aby uzyskać listę tych błędów, zobacz [errno](../../c-runtime-library/errno-constants.md). Kody błędów rzeczywiste generowany dla każdego warunku błędu przedstawiono w poniższej tabeli.

## <a name="error-conditions"></a>Warunki błędów

|*buffer*|*numberOfElements*|*sourceTime*|Zwraca|Wartość w *buforu*|
|--------------|------------------------|------------|------------|-----------------------|
|**NULL**|wszystkie|wszystkie|**EINVAL —**|Nie zmodyfikowano|
|Nie **NULL** (wskazuje prawidłowy pamięci)|0|wszystkie|**EINVAL —**|Nie zmodyfikowano|
|Nie **wartości NULL**|0 < < 26 rozmiaru|wszystkie|**EINVAL —**|Pusty ciąg|
|Nie **wartości NULL**|>= 26|NULL|**EINVAL —**|Pusty ciąg|
|Nie **wartości NULL**|>= 26|< 0|**EINVAL —**|Pusty ciąg|

## <a name="remarks"></a>Uwagi

**Ctime_s —** funkcja konwertuje przechowywanych jako wartość czasu [time_t —](../../c-runtime-library/standard-types.md) struktury na ciąg znaków. *SourceTime* wartość zazwyczaj jest uzyskiwana w wyniku wywołania [czas](time-time32-time64.md), która zwraca liczbę sekund, jaka upłynęła od północy (00: 00:00), 1 stycznia 1970, uniwersalny czas koordynowany (UTC). Zwracana wartość ciągu zawiera dokładnie 26 znaków i ma postać:

`Wed Jan 02 02:03:55 1980\n\0`

24-godzinnym jest używany. Wszystkie pola mają stałej szerokości. Znaku nowego wiersza (\n) i znak null ('\0') zajmują ostatnich dwóch pozycji w ciągu.

Ciąg przekonwertowany znaków jest również dostosowywana zgodnie z ustawieniami strefy czasu lokalnego. Zobacz [czasu](time-time32-time64.md), [_ftime —](ftime-ftime32-ftime64.md), i [localtime32_s —](localtime-s-localtime32-s-localtime64-s.md) funkcje informacji o konfigurowaniu czasu lokalnego oraz [_tzset —](tzset.md) Funkcja dla informacji na temat definiowania strefy czasowej środowiska i zmiennych globalnych.

**_wctime32_s —** i **_wctime64_s —** są wersja znaków dwubajtowych **_ctime32_s —** i **_ctime64_s —**; zwracającej wskaźnik na ciąg znaków dwubajtowych. W przeciwnym razie **_ctime64_s —**, **_wctime32_s —**, i **_wctime64_s —** zachowują się tak samo do **_ctime32_s —**.

**ctime_s —** jest wbudowaną funkcją, która daje w wyniku **_ctime64_s —** i **time_t —** jest odpowiednikiem **__time64_t —**. Aby wymusić kompilatora, aby zinterpretować **time_t —** jako starego 32-bitowych **time_t —**, można zdefiniować **_USE_32BIT_TIME_T**. To spowoduje **ctime_s —** mogła zwrócić **_ctime32_s —**. Nie jest to zalecane, ponieważ aplikacja może zakończyć się niepowodzeniem po 18 stycznia 2038 r., a nie jest dozwolona na platformach 64-bitowych.

W języku C++ za pomocą tych funkcji zostało uproszczone dzięki przeciążenia szablonu; przeciążeń można wnioskować o długości buforu automatycznie, co eliminuje konieczność określić argument rozmiar. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tctime_s —**|**ctime_s —**|**ctime_s —**|**_wctime_s**|
|**_tctime32_s —**|**_ctime32_s**|**_ctime32_s**|**_wctime32_s**|
|**_tctime64_s —**|**_ctime64_s —**|**_ctime64_s —**|**_wctime64_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**ctime_s —**, **_ctime32_s —**, **_ctime64_s —**|\<time.h>|
|**_wctime_s —**, **_wctime32_s —**, **_wctime64_s —**|\<Time.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).

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

## <a name="see-also"></a>Zobacz także

[Zarządzanie czasem](../../c-runtime-library/time-management.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
