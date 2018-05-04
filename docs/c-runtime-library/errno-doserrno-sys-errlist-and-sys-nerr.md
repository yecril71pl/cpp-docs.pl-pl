---
title: errno _doserrno —, _sys_errlist — i _sys_nerr — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _errno
apilocation:
- msvcrt.dll
apitype: DLLExport
f1_keywords:
- _sys_errlist
- errno
- _sys_nerr
- _doserrno
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b17abb975ea9f3212d4bd6171bcd2bffb78e483c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="errno-doserrno-syserrlist-and-sysnerr"></a>errno, _doserrno, _sys_errlist, and _sys_nerr
Makra globalne, które zawiera kody błędów, które są ustawiane podczas wykonywania programu i odpowiedniki ciągu kodów błędów do wyświetlenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
#define errno   (*_errno())  
#define _doserrno   (*__doserrno())  
#define _sys_errlist (__sys_errlist())  
#define _sys_nerr (*__sys_nerr())  
```  
  
## <a name="remarks"></a>Uwagi  
 Zarówno `errno` i `_doserrno` są ustawione na 0 w czasie wykonywania podczas uruchamiania programu. `errno` jest ustawiony na błąd w wywołaniu poziomie systemu. Ponieważ `errno` blokad wartość ostatniego wywołania, które go, ta wartość może zostać zmieniona przez pomyślne wywołania. Biblioteki wykonawczej wywołuje ten zestaw `errno` w przypadku wystąpienia błędu nie usuwaj `errno` w przypadku powodzenia. Wyczyść zawsze `errno` przez wywołanie metody `_set_errno(0)` bezpośrednio przed wywołaniem elementu, który może go ustawić i sprawdź go natychmiast po wywołaniu.  
  
 W przypadku wystąpienia błędu `errno` nie ustawiono niekoniecznie taką samą wartość jak kod błędu zwrócony przez wywołanie systemu. Dla operacji We/Wy `_doserrno` przechowuje odpowiedniki kod błędu systemu operacyjnego `errno` kodów. Dla większości operacji nie I/O wartości `_doserrno` nie jest ustawiona.  
  
 Każdy `errno` wartość jest skojarzony z komunikatem o błędzie w `_sys_errlist` można go wydrukować przy użyciu jednej z [perror](../c-runtime-library/reference/perror-wperror.md) funkcje lub przechowywane w ciągu przy użyciu jednej z [strerror —](../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md) lub [strerror_s —](../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md) funkcji. `perror` i `strerror` funkcje użyj `_sys_errlist` tablicy i `_sys_nerr`— liczba elementów w `_sys_errlist`— przetworzyć informacji o błędzie. Bezpośredni dostęp do `_sys_errlist` i `_sys_nerr` jest przestarzały ze względów bezpieczeństwa kodu. Zalecane jest użycie wersji bardziej bezpieczne, funkcjonalności zamiast globalne makra, jak pokazano poniżej:  
  
|Globalne — makro|Funkcjonalne odpowiedniki|  
|------------------|----------------------------|  
|`_doserrno`|[_get_doserrno —](../c-runtime-library/reference/get-doserrno.md), [_set_doserrno —](../c-runtime-library/reference/set-doserrno.md)|  
|`errno`|[_get_errno —](../c-runtime-library/reference/get-errno.md), [_set_errno —](../c-runtime-library/reference/set-errno.md)|  
|`_sys_errlist`, `_sys_nerr`|[strerror_s, _strerror_s, _wcserror_s, \__wcserror_s](../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md)|  
  
 Biblioteki matematyczne procedury zestaw `errno` przez wywołanie metody [_matherr —](../c-runtime-library/reference/matherr.md). Do obsługi błędów matematycznych inaczej, napisać własny procedury zgodnie z `_matherr` odwołania opis i nadaj mu nazwę `_matherr`.  
  
 Wszystkie `errno` wartościami w poniższej tabeli są stałe wstępnie zdefiniowanych w \<errno.h >, i są zgodne z systemem UNIX. Tylko `ERANGE`, `EILSEQ`, i `EDOM` są określone w normie ISO C99.  
  
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
  
|Globalne — makro|Wymagany nagłówek|Opcjonalne nagłówki|  
|------------------|---------------------|---------------------|  
|`errno`|\<errno.h > lub \<stdlib.h >, \<cerrno — > lub \<cstdlib — > (C++)||  
|`_doserrno`, `_sys_errlist`, `_sys_nerr`|\<stdlib.h>, \<cstdlib> (C++)|\<errno.h >, \<cerrno — > (C++)|  
  
 `_doserrno`, `_sys_errlist`, I `_sys_nerr` makra są rozszerzenia Microsoft. Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zmienne globalne](../c-runtime-library/global-variables.md)   
 [errno — stałe](../c-runtime-library/errno-constants.md)   
 [perror, _wperror —](../c-runtime-library/reference/perror-wperror.md)   
 [strerror —, _strerror —, _wcserror —, \__wcserror —](../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md)   
 [strerror_s —, _strerror_s —, _wcserror_s —, \__wcserror_s —](../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md)   
 [_get_doserrno](../c-runtime-library/reference/get-doserrno.md)   
 [_set_doserrno](../c-runtime-library/reference/set-doserrno.md)   
 [_get_errno](../c-runtime-library/reference/get-errno.md)   
 [_set_errno](../c-runtime-library/reference/set-errno.md)