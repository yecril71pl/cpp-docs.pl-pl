---
title: Wyjątki (C/C++)
ms.date: 11/04/2016
f1_keywords:
- ERROR_MOD_NOT_FOUND
- vcppException
- ERROR_SEVERITY_ERROR
helpviewer_keywords:
- vcppException
- C++ exception handling, delayed loading of DLLs
- delayed loading of DLLs, exceptions
- ERROR_SEVERITY_ERROR exception
- ERROR_MOD_NOT_FOUND exception
ms.assetid: c03be05d-1c39-4f35-84cf-00c9af3bae9a
ms.openlocfilehash: cf38af464f08e143ed9073befe30f6aeb8b913b6
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915462"
---
# <a name="exceptions-cc"></a>Wyjątki (C/C++)

Po napotkaniu błędów mogą być zgłaszane dwa kody wyjątków:

- W przypadku błędu funkcji **LoadLibrary**

- Dla błędu **GetProcAddress**

Oto informacje o wyjątku:

```
//
// Exception information
//
#define FACILITY_VISUALCPP  ((LONG)0x6d)
#define VcppException(sev,err)  ((sev) | (FACILITY_VISUALCPP<<16) | err)
```

Zgłoszone kody wyjątków to standardowe wartości VcppException (ERROR_SEVERITY_ERROR, ERROR_MOD_NOT_FOUND) i VcppException (ERROR_SEVERITY_ERROR, ERROR_PROC_NOT_FOUND). Wyjątek przekazuje wskaźnik do struktury **DelayLoadInfo** w wartości LPDWORD, która może zostać pobrana przez **GetExceptionInformation** w strukturze [EXCEPTION_RECORD](/windows/desktop/api/winnt/ns-winnt-exception_record) , ExceptionInformation [0].

Ponadto jeśli w polu grAttrs są ustawione nieprawidłowe bity, zostanie zgłoszony wyjątek ERROR_INVALID_PARAMETER. Ten wyjątek dotyczy wszystkich intencji i celów, które są krytyczne.

Zobacz [struktury i definicje stałe,](structure-and-constant-definitions.md) Aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz także

[Obsługa błędów oraz powiadomienia](error-handling-and-notification.md)
