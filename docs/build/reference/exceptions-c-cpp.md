---
title: "Wyjątki (C/C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ERROR_MOD_NOT_FOUND
- vcppException
- ERROR_SEVERITY_ERROR
dev_langs: C++
helpviewer_keywords:
- vcppException
- C++ exception handling, delayed loading of DLLs
- delayed loading of DLLs, exceptions
- ERROR_SEVERITY_ERROR exception
- ERROR_MOD_NOT_FOUND exception
ms.assetid: c03be05d-1c39-4f35-84cf-00c9af3bae9a
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 635e2b1406e9919425a396b6f49fe8eb6efd81eb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="exceptions-cc"></a>Wyjątki (C/C++)
Dwa kody wyjątków mogą być wywoływane, gdy zostaną napotkane błędy:  
  
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
  
 Kody wyjątków zgłoszonych są standardowe VcppException (error_severity_error —, error_mod_not_found —) i wartości VcppException (error_severity_error —, ERROR_PROC_NOT_FOUND). Wskaźnik do przekazuje wyjątek **DelayLoadInfo** struktury w wartości LPDWORD, który można pobrać przez **GetExceptionInformation** w [EXCEPTION_RECORD](http://msdn.microsoft.com/library/windows/desktop/aa363082) Struktura, pole ExceptionInformation [0].  
  
 Ponadto jeśli niepoprawne bity zostały ustawione w polu grAttrs, ERROR_INVALID_PARAMETER wyjątku. Ten wyjątek jest na wszystkich intents i purposes, krytyczny.  
  
 Zobacz [struktura i stała — definicje](../../build/reference/structure-and-constant-definitions.md) Aby uzyskać więcej informacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa błędów oraz powiadomienia](../../build/reference/error-handling-and-notification.md)