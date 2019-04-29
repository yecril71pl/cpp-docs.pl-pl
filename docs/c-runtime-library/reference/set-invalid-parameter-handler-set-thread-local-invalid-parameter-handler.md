---
title: _set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler
ms.date: 11/04/2016
apiname:
- _set_invalid_parameter_handler
- _set_thread_local_invalid_parameter_handler
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- set_invalid_parameter_handler
- _set_invalid_parameter_handler
- _set_thread_local_invalid_parameter_handler
helpviewer_keywords:
- invalid parameter handler
- set_invalid_parameter_handler function
- _set_invalid_parameter_handler function
- _set_thread_local_invalid_parameter_handler function
ms.assetid: c0e67934-1a41-4016-ad8e-972828f3ac11
ms.openlocfilehash: 1df876d6df9327e817d5d2c401e0abe97ad7a548
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356514"
---
# <a name="setinvalidparameterhandler-setthreadlocalinvalidparameterhandler"></a>_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler

Określa funkcję, która ma być wywoływana, gdy CRT wykrywa nieprawidłowy argument.

## <a name="syntax"></a>Składnia

```C
_invalid_parameter_handler _set_invalid_parameter_handler(
   _invalid_parameter_handler pNew
);
_invalid_parameter_handler _set_thread_local_invalid_parameter_handler(
   _invalid_parameter_handler pNew
);
```

### <a name="parameters"></a>Parametry

*pNew*<br/>
Wskaźnik funkcji na nowy program obsługi nieprawidłowego parametru.

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do obsługi nieprawidłowego parametru, przed wywołaniem.

## <a name="remarks"></a>Uwagi

Wiele funkcji środowiska uruchomieniowego C sprawdzania poprawności argumentów przekazanych do nich. Nieprawidłowy argument jest przekazywany, funkcja ustawić **errno** numer błędu lub zwracają kod błędu. W takich przypadkach procedura obsługi nieprawidłowego parametru jest również nazywany. Środowisko wykonawcze C dostarcza domyślne globalne nieprawidłowy program obsługi parametrów kończy program, który wyświetla komunikat o błędzie w czasie wykonywania. Możesz użyć **_set_invalid_parameter_handler —** można ustawić własną funkcję jako globalne nieprawidłowy parametr uchwytu. Środowisko wykonawcze języka C obsługuje również program obsługi nieprawidłowego parametru lokalnej wątku. Jeśli program obsługi parametrów lokalnej wątku można ustawić w wątku za pomocą **_set_thread_local_invalid_parameter_handler**, funkcje środowiska uruchomieniowego języka C, wywoływana z wątku, użyj tej procedury obsługi zamiast globalnego programu obsługi. Tylko jednej funkcji — można określić jako procedura obsługi globalnej nieprawidłowy argument w danym momencie. Można określić tylko jednej funkcji — jako procedura obsługi nieprawidłowy argument lokalnej wątku na wątek, ale inne wątki mogą mieć różne obsługi lokalnej wątku. Dzięki temu można zmienić obsługi używane w jednej części kodu, bez wywierania wpływu na działanie innych wątków.

Gdy środowisko uruchomieniowe wywołuje funkcję nieprawidłowego parametru, zwykle oznacza to, że wystąpił nieodwracalny błąd. Funkcja obsługi nieprawidłowego parametru, dostraczone należy zapisać wszystkie dane, można, a następnie Przerwij. Go nie powinny zwracać kontroli do funkcji main, chyba że masz pewność, że błąd jest możliwy do odzyskania.

Funkcja obsługi nieprawidłowego parametru, musi mieć poniższy prototyp:

```C
void _invalid_parameter(
   const wchar_t * expression,
   const wchar_t * function,
   const wchar_t * file,
   unsigned int line,
   uintptr_t pReserved
);
```

*Wyrażenie* argument jest szeroki ciąg reprezentujący wyrażenie argumentu, który spowodował błąd. *Funkcja* argument jest nazwą funkcji CRT, który otrzymał nieprawidłowy argument. *Pliku* argument jest nazwą pliku źródłowego CRT, która zawiera funkcję. *Wiersza* argument jest numer wiersza, w tym pliku. Ostatni argument jest zarezerwowana. Wszystkie parametry mają wartość **NULL** chyba że używana jest wersja do debugowania biblioteki CRT.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_set_invalid_parameter_handler —**, **_set_thread_local_invalid_parameter_handler**|C: \<stdlib.h><br /><br /> C++: \<cstdlib — > lub \<stdlib.h >|

**_Set_invalid_parameter_handler —** i **_set_thread_local_invalid_parameter_handler** funkcje są specyficzne dla firmy Microsoft. Aby uzyskać informacje o zgodności – zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

W poniższym przykładzie procedura obsługi nieprawidłowego parametru błędów służy do drukowania funkcji, który otrzymał nieprawidłowy parametr i pliku i wierszu w źródłach CRT. Gdy jest używana biblioteka debugowania CRT, nieprawidłowy parametr błędy też wiązać się z potwierdzenie, która jest wyłączona w tym przykładzie, korzystając [_CrtSetReportMode](crtsetreportmode.md).

```C
// crt_set_invalid_parameter_handler.c
// compile with: /Zi /MTd
#include <stdio.h>
#include <stdlib.h>
#include <crtdbg.h>  // For _CrtSetReportMode

void myInvalidParameterHandler(const wchar_t* expression,
   const wchar_t* function,
   const wchar_t* file,
   unsigned int line,
   uintptr_t pReserved)
{
   wprintf(L"Invalid parameter detected in function %s."
            L" File: %s Line: %d\n", function, file, line);
   wprintf(L"Expression: %s\n", expression);
   abort();
}

int main( )
{
   char* formatString;

   _invalid_parameter_handler oldHandler, newHandler;
   newHandler = myInvalidParameterHandler;
   oldHandler = _set_invalid_parameter_handler(newHandler);

   // Disable the message box for assertions.
   _CrtSetReportMode(_CRT_ASSERT, 0);

   // Call printf_s with invalid parameters.

   formatString = NULL;
   printf(formatString);
}
```

```Output
Invalid parameter detected in function common_vfprintf. File: minkernel\crts\ucrt\src\appcrt\stdio\output.cpp Line: 32
Expression: format != nullptr
```

## <a name="see-also"></a>Zobacz także

[_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler](get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)<br/>
[Wersje funkcji CRT z rozszerzonymi zabezpieczeniami](../../c-runtime-library/security-enhanced-versions-of-crt-functions.md)<br/>
[errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
