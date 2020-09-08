---
title: _set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler
description: Dokumentacja interfejsu API dla _set_invalid_parameter_handler i _set_thread_local_invalid_parameter_handler; Ustawia funkcję, która ma być wywoływana, gdy CRT wykryje nieprawidłowy argument.
ms.date: 4/2/2020
api_name:
- _set_invalid_parameter_handler
- _set_thread_local_invalid_parameter_handler
- _o__set_invalid_parameter_handler
- _o__set_thread_local_invalid_parameter_handler
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: a965bd71af18a57c31d3cfef927be02005c407c0
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555621"
---
# <a name="_set_invalid_parameter_handler-_set_thread_local_invalid_parameter_handler"></a>_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler

Ustawia funkcję, która ma być wywoływana, gdy CRT wykryje nieprawidłowy argument.

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
Wskaźnik funkcji do nowego nieprawidłowego parametru procedury obsługi.

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do procedury obsługi nieprawidłowego parametru przed wywołaniem.

## <a name="remarks"></a>Uwagi

Wiele funkcji środowiska uruchomieniowego języka C sprawdza poprawność argumentów przekazane do nich. Jeśli przeszedł nieprawidłowy argument, funkcja może ustawić numer błędu **errno** lub zwrócić kod błędu. W takich przypadkach jest również wywoływana procedura obsługi nieprawidłowego parametru. Środowisko uruchomieniowe języka C udostępnia domyślną globalną procedurę obsługi nieprawidłowego parametru, która kończy program i wyświetla komunikat o błędzie środowiska uruchomieniowego. Za pomocą **_set_invalid_parameter_handler** można ustawić własną funkcję jako procedurę obsługi nieprawidłowego parametru. Środowisko uruchomieniowe języka C obsługuje również procedurę obsługi nieprawidłowego parametru w wątku. Jeśli program obsługi parametrów lokalnych wątku jest ustawiony w wątku przy użyciu **_set_thread_local_invalid_parameter_handler**, funkcja środowiska uruchomieniowego języka C wywołana z wątku używa tego programu obsługi zamiast globalnego programu obsługi. Tylko jedną funkcję można określić jako globalną procedurę obsługi nieprawidłowego argumentu. Tylko jedną funkcję można określić jako procedurę obsługi nieprawidłowego argumentu w wątku dla wątku, ale różne wątki mogą mieć różne procedury obsługi wątków lokalnych. Pozwala to na zmianę procedury obsługi używanej w jednej części kodu bez wpływu na zachowanie innych wątków.

Gdy środowisko uruchomieniowe wywołuje nieprawidłową funkcję parametru, zazwyczaj oznacza to, że wystąpił nieodwracalny błąd. Podaną funkcję procedury obsługi nieprawidłowego parametru należy zapisać wszystkie dane, które mogą, a następnie przerwać. Nie powinna zwracać kontroli do funkcji Main, o ile nie masz pewności, że błąd jest możliwy do odzyskania.

Funkcja obsługi nieprawidłowego parametru musi mieć następujący prototyp:

```C
void _invalid_parameter(
   const wchar_t * expression,
   const wchar_t * function,
   const wchar_t * file,
   unsigned int line,
   uintptr_t pReserved
);
```

Argument *Expression* jest dwuciągową reprezentacją wyrażenia argumentu, które zgłosiło błąd. Argument *funkcji* jest nazwą funkcji CRT, która odebrała nieprawidłowy argument. Argument *pliku* jest nazwą pliku źródłowego CRT, który zawiera funkcję. Argument *wiersza* jest numerem wiersza w tym pliku. Ostatni argument jest zarezerwowany. Wszystkie parametry mają wartość **null** , chyba że jest używana wersja debugowania biblioteki CRT.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_set_invalid_parameter_handler**, **_set_thread_local_invalid_parameter_handler**|S \<stdlib.h><br /><br /> C++: \<cstdlib> lub \<stdlib.h>|

**_Set_invalid_parameter_handler** i **_set_thread_local_invalid_parameter_handler** funkcje są specyficzne dla firmy Microsoft. Aby uzyskać informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

W poniższym przykładzie procedura obsługi błędów nieprawidłowego parametru jest używana do drukowania funkcji, która otrzymała nieprawidłowy parametr i plik i wiersz w źródłach CRT. Gdy jest używana Biblioteka CRT debugowania, nieprawidłowe błędy parametrów również zgłaszają potwierdzenie, które jest wyłączone w tym przykładzie przy użyciu [_CrtSetReportMode](crtsetreportmode.md).

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

## <a name="see-also"></a>Zobacz też

[_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler](get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)<br/>
[Wersje funkcji CRT z rozszerzonymi zabezpieczeniami](../../c-runtime-library/security-enhanced-versions-of-crt-functions.md)<br/>
[errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
