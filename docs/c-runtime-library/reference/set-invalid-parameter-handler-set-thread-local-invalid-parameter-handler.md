---
title: "_set_invalid_parameter_handler —, _set_thread_local_invalid_parameter_handler | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- invalid parameter handler
- set_invalid_parameter_handler function
- _set_invalid_parameter_handler function
- _set_thread_local_invalid_parameter_handler function
ms.assetid: c0e67934-1a41-4016-ad8e-972828f3ac11
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7827b8c538a90c39c0dc32320aaab01ada7e2318
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="setinvalidparameterhandler-setthreadlocalinvalidparameterhandler"></a>_set_invalid_parameter_handler —, _set_thread_local_invalid_parameter_handler
Ustawia funkcja wywoływana, gdy CRT wykrywa nieprawidłowy argument.  
  
## <a name="syntax"></a>Składnia  
  
```  
_invalid_parameter_handler _set_invalid_parameter_handler(  
   _invalid_parameter_handler pNew  
);  
_invalid_parameter_handler _set_thread_local_invalid_parameter_handler(  
   _invalid_parameter_handler pNew  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `pNew`  
 Wskaźnik funkcji do nowy program obsługi nieprawidłowych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do program obsługi nieprawidłowych parametrów przed wywołaniem.  
  
## <a name="remarks"></a>Uwagi  
 Wiele funkcji środowiska wykonawczego języka C sprawdzania poprawności Argumenty przekazane do nich. Jeśli podano nieprawidłowy argument zostanie przekazany, można ustawić funkcję `errno` numeru błędu lub zwracany kod błędu. W takich przypadkach program obsługi nieprawidłowych parametrów skrót. Środowisko uruchomieniowe C udostępnia domyślny globalny nieprawidłowy parametr program obsługi kończy program, który wyświetla komunikat o błędzie środowiska wykonawczego. Można użyć `_set_invalid_parameter_handler` można ustawić jako program obsługi nieprawidłowych parametrów globalnych własnych funkcji. Środowisko uruchomieniowe C obsługuje również obsługi lokalnej wątku nieprawidłowy parametr. Jeśli parametr lokalnej wątku jest ustawiony program obsługi w wątku przy użyciu `_set_thread_local_invalid_parameter_handler`, funkcje środowiska wykonawczego języka C wywołać z wątku Użyj programu obsługi zamiast globalnego programu obsługi. Tylko jednej funkcji można określić jako program obsługi globalne nieprawidłowy argument w czasie. Można określić tylko jedną funkcję jako program obsługi nieprawidłowy argument lokalnej wątku na wątek, ale inne wątki mogą mieć różne obsługi lokalnej wątku. Dzięki temu można zmienić obsługi używane w jednej części kodu bez wpływu na zachowanie inne wątki.  
  
 Gdy środowiska uruchomieniowego wywołuje funkcję nieprawidłowy parametr, zwykle oznacza to, że wystąpił nieodwracalny błąd. Funkcji obsługi nieprawidłowy parametr, który podasz należy zapisywać żadnych danych może, a następnie przerwania. Nie powinien zwracać sterowania funkcji main Jeśli nie ma pewności, czy błąd jest możliwe do odzyskania.  
  
 Nieprawidłowy parametr funkcji obsługi musi mieć następujące prototypu:  
  
```  
void _invalid_parameter(  
   const wchar_t * expression,  
   const wchar_t * function,   
   const wchar_t * file,   
   unsigned int line,  
   uintptr_t pReserved  
);  
```  
  
 `expression` Argument to reprezentacja ciągu typu wide wyrażenie argumentu, który zgłoszony błąd. `function` Argument jest nazwą funkcji CRT, który odebrał nieprawidłowy argument. `file` Argument jest nazwą pliku źródłowego CRT, która zawiera funkcję. `line` Argument jest numer wiersza, w tym pliku. Ostatni argument jest zarezerwowana. Wszystkie parametry mają wartość `NULL` chyba że używana jest wersja biblioteki CRT do debugowania.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_set_invalid_parameter_handler`, `_set_thread_local_invalid_parameter_handler`|C: \<stdlib.h><br /><br /> C++: \<cstdlib — > lub \<stdlib.h >|  
  
 `_set_invalid_parameter_handler` i `_set_thread_local_invalid_parameter_handler` funkcje są określone firmy Microsoft. Aby uzyskać informacje dotyczące zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie program obsługi nieprawidłowych parametrów błąd służy do drukowania funkcji, które odebrano nieprawidłowy parametr i plików i wierszy w CRT źródeł. W przypadku bibliotek debugowania CRT nieprawidłowy parametr błędy też wiązać się z potwierdzeniem, która jest wyłączona w tym przykładzie przy użyciu [_crtsetreportmode —](../../c-runtime-library/reference/crtsetreportmode.md).  
  
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
 [_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler](../../c-runtime-library/reference/get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)   
 [Wersje funkcji CRT z rozszerzonymi zabezpieczeniami](../../c-runtime-library/security-enhanced-versions-of-crt-functions.md)   
 [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)