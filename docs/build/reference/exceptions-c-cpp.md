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
ms.openlocfilehash: 9c86d99b365994870b991967b6cab6e6ee5c5088
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422991"
---
# <a name="exceptions-cc"></a>Wyjątki (C/C++)

Dwa kody wyjątków może być wywoływane, gdy zostaną napotkane błędy:

- Aby uzyskać **LoadLibrary** awarii

- Aby uzyskać **GetProcAddress** awarii

Poniżej przedstawiono informacje o wyjątku:

```
//
// Exception information
//
#define FACILITY_VISUALCPP  ((LONG)0x6d)
#define VcppException(sev,err)  ((sev) | (FACILITY_VISUALCPP<<16) | err)
```

Kody wyjątków, zgłaszane są standardowe VcppException (error_severity_error —, error_mod_not_found —) i wartości VcppException (error_severity_error —, ERROR_PROC_NOT_FOUND). Wyjątek przekazuje wskaźnik do **DelayLoadInfo** struktury LPDWORD wartości, które mogą być pobierane według **GetExceptionInformation** w [EXCEPTION_RECORD](/windows/desktop/api/winnt/ns-winnt-_exception_record) Struktura, pole ExceptionInformation [0].

Ponadto jeśli niepoprawne bity są ustawione w polu grAttrs, ERROR_INVALID_PARAMETER wyjątku. Ten wyjątek jest na wszystkich intents i purposes, krytyczny.

Zobacz [struktura i stała — definicje](../../build/reference/structure-and-constant-definitions.md) Aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz także

[Obsługa błędów oraz powiadomienia](../../build/reference/error-handling-and-notification.md)
