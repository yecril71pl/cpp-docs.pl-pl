---
title: _set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 0637937d4596d28875c40efec62f79a32f533dcf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337682"
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

*pNowy*<br/>
Wskaźnik funkcji do nowego nieprawidłowego programu obsługi parametrów.

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do nieprawidłowego programu obsługi parametrów przed wywołaniem.

## <a name="remarks"></a>Uwagi

Wiele funkcji środowiska wykonawczego C sprawdzić ważność argumentów przekazanych do nich. Jeśli nieprawidłowy argument zostanie przekazany, funkcja może ustawić numer błędu **errno** lub zwrócić kod błędu. W takich przypadkach wywoływany jest również nieprawidłowy program obsługi parametrów. Środowisko wykonawcze języka C dostarcza domyślny globalny nieprawidłowy program obsługi parametrów, który kończy program i wyświetla komunikat o błędzie środowiska uruchomieniowego. Za pomocą **_set_invalid_parameter_handler** można ustawić własną funkcję jako globalny nieprawidłowy program obsługi parametrów. Środowisko wykonawcze języka C obsługuje również program obsługi nieprawidłowych parametrów lokalnych wątku. Jeśli program obsługi parametrów lokalnych wątku jest ustawiony w wątku przy użyciu **_set_thread_local_invalid_parameter_handler**, funkcje środowiska wykonawczego C wywoływane z wątku użyć tego programu obsługi zamiast globalnego programu obsługi. Tylko jedna funkcja może być określona jako globalny nieprawidłowy argument obsługi w czasie. Tylko jedna funkcja może być określona jako obsługi nieprawidłowy argument wątku na wątek, ale różne wątki mogą mieć różne programy obsługi lokalne wątku. Dzięki temu można zmienić program obsługi używany w jednej części kodu bez wpływu na zachowanie innych wątków.

Gdy środowisko wykonawcze wywołuje funkcję nieprawidłowego parametru, zwykle oznacza to, że wystąpił błąd nienaprawialny. Nieprawidłowa funkcja obsługi parametrów, którą podano, powinna zapisać wszystkie dane, które może, a następnie przerwać. Nie należy zwracać kontroli do funkcji głównej, chyba że masz pewność, że błąd jest możliwe do odzyskania.

Nieprawidłowa funkcja obsługi parametrów musi mieć następujący prototyp:

```C
void _invalid_parameter(
   const wchar_t * expression,
   const wchar_t * function,
   const wchar_t * file,
   unsigned int line,
   uintptr_t pReserved
);
```

Argument *wyrażenia* jest szeroką reprezentacją ciągu wyrażenia argumentu, który wywołał błąd. Argument *funkcji* jest nazwą funkcji CRT, która otrzymała nieprawidłowy argument. Argument *pliku* jest nazwą pliku źródłowego CRT, który zawiera funkcję. Argument *wiersza* jest numerem wiersza w tym pliku. Ostatni argument jest zarezerwowany. Wszystkie parametry mają wartość **NULL,** chyba że używana jest wersja debugowania biblioteki CRT.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_set_invalid_parameter_handler** **, _set_thread_local_invalid_parameter_handler**|C: \<> stdlib.h<br /><br /> C++: \<cstdlib> lub \<stdlib.h>|

Funkcje **_set_invalid_parameter_handler** i **_set_thread_local_invalid_parameter_handler** są specyficzne dla firmy Microsoft. Aby uzyskać informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

W poniższym przykładzie nieprawidłowy program obsługi błędów parametrów jest używany do drukowania funkcji, która otrzymała nieprawidłowy parametr oraz plik i wiersz w źródłach CRT. Gdy używana jest biblioteka CRT debugowania, nieprawidłowe błędy parametrów również podnieść twierdzenie, które jest wyłączone w tym przykładzie przy użyciu [_CrtSetReportMode](crtsetreportmode.md).

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
[Ulepszone pod względem zabezpieczeń wersje funkcji CRT](../../c-runtime-library/security-enhanced-versions-of-crt-functions.md)<br/>
[errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
