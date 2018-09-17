---
title: Wyjątki (C/C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- ERROR_MOD_NOT_FOUND
- vcppException
- ERROR_SEVERITY_ERROR
dev_langs:
- C++
helpviewer_keywords:
- vcppException
- C++ exception handling, delayed loading of DLLs
- delayed loading of DLLs, exceptions
- ERROR_SEVERITY_ERROR exception
- ERROR_MOD_NOT_FOUND exception
ms.assetid: c03be05d-1c39-4f35-84cf-00c9af3bae9a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7d32b22d0ac8a065d59030dccd144236a79c6ac8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705696"
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

## <a name="see-also"></a>Zobacz też

[Obsługa błędów oraz powiadomienia](../../build/reference/error-handling-and-notification.md)