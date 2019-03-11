---
title: Sprawdzanie poprawności parametru
ms.date: 11/04/2016
helpviewer_keywords:
- parameters, validation
ms.assetid: 019dd5f0-dc61-4d2e-b4e9-b66409ddf1f2
ms.openlocfilehash: 2c7b2ae50fdcbf59cd23cc309a4ddc4c0803e24e
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57748427"
---
# <a name="parameter-validation"></a>Sprawdzanie poprawności parametru

Większość funkcji CRT z rozszerzonymi zabezpieczeniami i wiele z istniejących funkcji sprawdzają poprawność swoich parametrów. Może to obejmować sprawdzenie wskaźniki **NULL**, sprawdzanie, czy liczby całkowite dzielą się na prawidłowym zakresem lub Sprawdzanie, czy wartości wyliczenia są prawidłowe. W przypadku odnalezienia nieprawidłowy parametr jest wykonywana procedura obsługi nieprawidłowego parametru.

## <a name="invalid-parameter-handler-routine"></a>Procedura obsługi nieprawidłowego parametru

Gdy funkcja biblioteki wykonawczej C wykryje nieprawidłowy parametr, jego przechwytuje niektóre informacje o błędzie, a następnie wywołuje makro, który opakowuje funkcję wysyłania obsługi nieprawidłowego parametru, jeden z [_invalid_parameter](../c-runtime-library/reference/invalid-parameter-functions.md), [_invalid_parameter_noinfo](../c-runtime-library/reference/invalid-parameter-functions.md), lub [_invalid_parameter_noinfo_noreturn](../c-runtime-library/reference/invalid-parameter-functions.md). Wywołana funkcja wysyłania jest zależna od tego, czy kod jest odpowiednio do kompilacji debugowanej, kompilacji detalicznej lub błąd nie jest uważany za możliwe do odzyskania.

W kompilacjach do debugowania makro nieprawidłowy parametr zwykle wywołuje potwierdzenie nie powiodło się i punkt przerwania debugera przed wywołaniem funkcji wysyłania. Gdy kod jest wykonywany, potwierdzenie może być zgłaszany użytkownikowi w oknie dialogowym "Przerwij", "Spróbuj ponownie" i "Kontynuuj" lub podobne możliwości, w zależności od wersji biblioteki systemu operacyjnego i środowiska uruchomieniowego. Te opcje umożliwiają użytkownikowi natychmiast zakończyć program, aby dołączyć debuger lub pozwolić programowi istniejącego kodu będą nadal działać, która wywołuje funkcję wysyłania.

Funkcja wysyłania procedurę obsługi nieprawidłowego parametru, z kolei wywołuje aktualnie przypisanych nieprawidłowy parametr uchwytu. Domyślnie wywołuje nieprawidłowy parametr `_invoke_watson` który powoduje, że aplikacja "awarii", oznacza to, zakończenia i wygenerować minizrzut. Jeśli włączona przez system operacyjny, okno dialogowe prosi użytkownika czy chce załadować zrzutu awaryjnego do firmy Microsoft do analizy.

To zachowanie można zmienić za pomocą funkcji [_set_invalid_parameter_handler —](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) lub [_set_thread_local_invalid_parameter_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) ustawić program obsługi nieprawidłowych parametrów własnej funkcji. W przypadku funkcji, które określisz nie zakończyć aplikację, zwróceniem sterowania do funkcji, który otrzymał nieprawidłowe parametry. W CRT, funkcje te zwykle przestanie wykonywania funkcji Ustaw `errno` kod błędu i zwracają kod błędu. W wielu przypadkach `errno` wartość i wartość zwracana to `EINVAL`, wskazując nieprawidłowy parametr. W niektórych przypadkach dokładniejszą kod błędu jest zwracany, takich jak `EBADF` dla złym wskaźnikiem pliku przekazany jako parametr. Aby uzyskać więcej informacji na temat `errno`, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="see-also"></a>Zobacz także

[Funkcje zabezpieczeń w CRT](../c-runtime-library/security-features-in-the-crt.md)<br/>
[Biblioteka CRT, funkcje](../c-runtime-library/crt-library-features.md)
