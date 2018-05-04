---
title: Sprawdzanie poprawności parametru | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- parameters, validation
ms.assetid: 019dd5f0-dc61-4d2e-b4e9-b66409ddf1f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a89ec2cd0b360f498e52af7e49bd5c6571521e2c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="parameter-validation"></a>Walidacja parametru
Większość funkcji CRT z rozszerzonymi zabezpieczeniami i wielu istniejących funkcji sprawdza poprawność ich parametrów. Może to obejmować sprawdzania wskaźników NULL, sprawdzanie, czy można podzielić na prawidłowy zakres liczb całkowitych lub Sprawdzanie, czy wartości wyliczenia są prawidłowe. Program obsługi nieprawidłowych parametrów jest wykonywany, gdy znaleziono nieprawidłowy parametr.  
  
## <a name="invalid-parameter-handler-routine"></a>Nieprawidłowy parametr procedury obsługi  
 Funkcja biblioteki wykonawczej C wykrycie nieprawidłowy parametr go przechwytuje niektóre informacje o błędzie, a następnie wywołuje makra, który opakowuje funkcję wysyłania obsługi nieprawidłowy parametr, jeden z [_invalid_parameter](../c-runtime-library/reference/invalid-parameter-functions.md), [_invalid_parameter_noinfo](../c-runtime-library/reference/invalid-parameter-functions.md), lub [_invalid_parameter_noinfo_noreturn](../c-runtime-library/reference/invalid-parameter-functions.md). Wywołana funkcja wysyłania zależy od tego, czy kod jest odpowiednio kompilację debugowania, kompilację detalicznych lub błąd nie jest uważana za możliwe do odzyskania. 
 
 W kompilacjach do debugowania makro nieprawidłowy parametr zwykle zgłasza potwierdzenia nie powiodło się i przerwania debugera przed wywołaniem funkcji wysyłania. Po wykonaniu kod potwierdzenia może być zgłaszany do użytkownika w oknie dialogowym "Abort", "Ponów" i "Continue" lub podobne opcje, w zależności od wersji biblioteki systemu operacyjnego i środowiska uruchomieniowego. Te opcje umożliwiają użytkownikom natychmiast zakończyć program, aby dołączyć debuger lub pozwolić programowi istniejący kod nadal działać, który wywołuje funkcję wysyłania. 
 
 Funkcja wysyłania obsługi nieprawidłowy parametr z kolei wywołuje program obsługi aktualnie przypisanej nieprawidłowy parametr. Domyślnie wywołuje nieprawidłowy parametr `_invoke_watson` co powoduje, że aplikacja "awarię", oznacza to, przerwanie i generowanie mini zrzutu. Jeśli włączona przez system operacyjny, okno dialogowe pyta użytkownika czy chce załadować zrzutu awaryjnego do firmy Microsoft do analizy.   
  
 To zachowanie można zmienić za pomocą funkcji [_set_invalid_parameter_handler —](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) lub [_set_thread_local_invalid_parameter_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) ustawić programu obsługi nieprawidłowy parametr do własnych funkcji. Jeśli funkcja, które określisz nie zakończyć aplikację, zwróceniem sterowania do funkcji, która odebrała nieprawidłowe parametry. W CRT, te funkcje przestaną zwykle wykonanie funkcji Ustaw `errno` kod błędu i zwracany kod błędu. W wielu przypadkach `errno` wartości i wartości zwracanej są `EINVAL`, wskazując nieprawidłowy parametr. W niektórych przypadkach bardziej szczegółowe kod błędu jest zwracany, takich jak `EBADF` dla nieprawidłowego pliku wskaźnik przekazany jako parametr. Aby uzyskać więcej informacji na temat `errno`, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje zabezpieczeń w CRT](../c-runtime-library/security-features-in-the-crt.md)   
 [Biblioteka CRT, funkcje](../c-runtime-library/crt-library-features.md)