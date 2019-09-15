---
title: errno, _doserrno, _sys_errlist, and _sys_nerr
ms.date: 11/04/2016
api_name:
- _errno
api_location:
- msvcrt.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _sys_errlist
- errno
- _sys_nerr
- _doserrno
helpviewer_keywords:
- error codes, printing
- sys_errlist global variable
- doserrno global variable
- errno global variable
- _doserrno global variable
- _sys_errlist global variable
- _sys_nerr global variable
- sys_nerr global variable
ms.assetid: adbec641-6d91-4e19-8398-9a34046bd369
ms.openlocfilehash: 5b10d98dab41151290d4e44e031f659108b0c73c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944554"
---
# <a name="errno-_doserrno-_sys_errlist-and-_sys_nerr"></a>errno, _doserrno, _sys_errlist, and _sys_nerr

Makra globalne, które zawierają kody błędów, które są ustawiane podczas wykonywania programu, oraz odpowiedników ciągów kodów błędów do wyświetlenia.

## <a name="syntax"></a>Składnia

```
#define errno   (*_errno())
#define _doserrno   (*__doserrno())
#define _sys_errlist (__sys_errlist())
#define _sys_nerr (*__sys_nerr())
```

## <a name="remarks"></a>Uwagi

Oba `errno` i`_doserrno` są ustawione na 0 przez środowisko uruchomieniowe podczas uruchamiania programu. `errno`jest ustawiony na błąd w wywołaniu na poziomie systemu. Ponieważ `errno` przechowuje wartość dla ostatniego wywołania, które go ustawi, ta wartość może zostać zmieniona przez pomyślne wywołania. Wywołania biblioteki czasu wykonywania ustawione `errno` dla błędu nie są czyszczone `errno` po pomyślnym zalogowaniu. Zawsze czyść `errno` , wywołując `_set_errno(0)` bezpośrednio przed wywołaniem, które może go ustawić, i sprawdź je bezpośrednio po wywołaniu.

W przypadku błędu `errno` nie musi być ustawiona taka sama wartość jak kod błędu zwracany przez wywołanie systemowe. W przypadku operacji we/wy `_doserrno` program przechowuje równoważne `errno` kody kodów błędów systemu operacyjnego. W przypadku większości operacji innych niż we/wy wartość `_doserrno` nie jest ustawiona.

Każda `errno` wartość jest skojarzona z komunikatem o `_sys_errlist` błędzie w programie, który można wydrukować przy użyciu jednej z funkcji [pError](../c-runtime-library/reference/perror-wperror.md) lub przechowywanych w ciągu przy użyciu jednej z funkcji [strerror](../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md) lub [strerror_s](../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md) . `_sys_nerr` `_sys_errlist`Funkcje `perror` i`strerror` wykorzystują`_sys_errlist` tablicę i — liczbę elementów w — do przetwarzania informacji o błędach. Bezpośredni dostęp do `_sys_errlist` i `_sys_nerr` jest przestarzały ze względu na zabezpieczenia kodu. Zalecamy korzystanie z bezpieczniejszych wersji funkcjonalnych zamiast makr globalnych, jak pokazano poniżej:

|Makro globalne|Funkcjonalne odpowiedniki|
|------------------|----------------------------|
|`_doserrno`|[_get_doserrno](../c-runtime-library/reference/get-doserrno.md), [_set_doserrno](../c-runtime-library/reference/set-doserrno.md)|
|`errno`|[_get_errno](../c-runtime-library/reference/get-errno.md), [_set_errno](../c-runtime-library/reference/set-errno.md)|
|`_sys_errlist`, `_sys_nerr`|[strerror_s, _strerror_s, _wcserror_s, \__wcserror_s](../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md)|

Procedury matematyczne biblioteki ustawione `errno` przez wywołanie [_matherr](../c-runtime-library/reference/matherr.md). Aby obsłużyć błędy matematyczne w inny sposób, napisz własną procedurę `_matherr` zgodnie z opisem odwołania i `_matherr`nadaj jej nazwę.

Wszystkie `errno` wartości w poniższej tabeli są wstępnie zdefiniowanymi stałymi w \<errno. h > i są zgodne z systemem UNIX. Tylko `ERANGE`, `EILSEQ` i`EDOM` są określone w standardzie ISO C99.

|Stała|Systemowy komunikat o błędzie|Wartość|
|--------------|--------------------------|-----------|
|`EPERM`|Operacja niedozwolona|1|
|`ENOENT`|Nie ma takiego pliku lub katalogu|2|
|`ESRCH`|Nie ma takiego procesu|3|
|`EINTR`|Funkcja przerwana|4|
|`EIO`|Błąd We/Wy|5|
|`ENXIO`|Nie ma takiego urządzenia lub adresu|6|
|`E2BIG`|Lista argumentów jest za długa|7|
|`ENOEXEC`|Błąd formatu pliku wykonywalnego|8|
|`EBADF`|Zły numer pliku|9|
|`ECHILD`|Brak procesów zduplikowanych|10|
|`EAGAIN`|Brak procesów lub za mało pamięci, lub osiągnięto maksymalny poziom zagnieżdżenia|11|
|`ENOMEM`|Za mało pamięci|12|
|`EACCES`|Odmowa uprawnień|13|
|`EFAULT`|Zły adres|14|
|`EBUSY`|Urządzenie lub zasoby są zajęte|16|
|`EEXIST`|Plik istnieje|17|
|`EXDEV`|Łącze między urządzeniami|18|
|`ENODEV`|Nie ma takiego urządzenia|19|
|`ENOTDIR`|Nie jest katalogiem|20|
|`EISDIR`|Jest katalogiem|21|
|`EINVAL`|Nieprawidłowy argument|22|
|`ENFILE`|Zbyt wiele otwartych plików w systemie|23|
|`EMFILE`|Zbyt wiele otwartych plików|24|
|`ENOTTY`|Niewłaściwe działanie sterowania We/Wy|25|
|`EFBIG`|Plik jest za duży|27|
|`ENOSPC`|Nie ma miejsca na urządzeniu|28|
|`ESPIPE`|Nieprawidłowe wyszukiwanie|29|
|`EROFS`|System plików tylko do odczytu|30|
|`EMLINK`|Za dużo łączy|31|
|`EPIPE`|Potok jest przerwany|32|
|`EDOM`|Argument matematyczny|33|
|`ERANGE`|Wynik za duży|34|
|`EDEADLK`|Wystąpiłoby zakleszczenie zasobu|36|
|`EDEADLOCK`|Tak samo jak EDEADLK w celu zachowania zgodności z poprzednimi wersjami Microsoft C|36|
|`ENAMETOOLONG`|Za długa nazwa pliku|38|
|`ENOLCK`|Blokady nie są dostępne|39|
|`ENOSYS`|Funkcja nieobsługiwana|40|
|`ENOTEMPTY`|Katalog nie jest pusty|41|
|`EILSEQ`|Nieprawidłowa sekwencja bajtów|42|
|`STRUNCATE`|Obcięto ciąg|80|

## <a name="requirements"></a>Wymagania

|Makro globalne|Wymagany nagłówek|Opcjonalny nagłówek|
|------------------|---------------------|---------------------|
|`errno`|\<errno. h > lub \<STDLIB. h >, \<cerrno > lub \<cstdlib > (C++)||
|`_doserrno`, `_sys_errlist`, `_sys_nerr`|\<stdlib.h>, \<cstdlib> (C++)|\<errno. h >, \<cerrno > (C++)|

Makra `_doserrno`, `_sys_errlist` i`_sys_nerr` są rozszerzeniami firmy Microsoft. Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Zmienne globalne](../c-runtime-library/global-variables.md)<br/>
[errno, stałe](../c-runtime-library/errno-constants.md)<br/>
[perror, _wperror](../c-runtime-library/reference/perror-wperror.md)<br/>
[strerror, _strerror, _wcserror, \__wcserror](../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md)<br/>
[strerror_s, _strerror_s, _wcserror_s, \__wcserror_s](../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md)<br/>
[_get_doserrno](../c-runtime-library/reference/get-doserrno.md)<br/>
[_set_doserrno](../c-runtime-library/reference/set-doserrno.md)<br/>
[_get_errno](../c-runtime-library/reference/get-errno.md)<br/>
[_set_errno](../c-runtime-library/reference/set-errno.md)
