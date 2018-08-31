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
ms.openlocfilehash: 40a3a9e1cf1384603d6b7d95fa5960e951f932ef
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43216886"
---
# <a name="exceptions-cc"></a>Wyjątki (C/C++)
Dwa kody wyjątków może być wywoływane, gdy zostaną napotkane błędy:  
  
-   Aby uzyskać **LoadLibrary** awarii  
  
-   Aby uzyskać **GetProcAddress** awarii  
  
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