---
title: "Eksportowanie funkcji języka C do użycia w C lub plików wykonywalnych języka C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- functions [C], exporting
- functions [C], C or C++ executables and
- __cplusplus macro
- exporting DLLs [C++], C functions in C++ executables
- exporting functions [C++], C functions in C++ executables
ms.assetid: b51d6e5e-37cf-4c1c-b0bf-fcf188c82f00
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 232cfb3a65dfe3e65eaa2eeef0a4a55e723b7f7d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="exporting-c-functions-for-use-in-c-or-c-language-executables"></a>Eksportowanie funkcji języka C do użycia w plikach wykonywalnych języka C lub C++  
  
Jeśli w bibliotece DLL napisane w języku C, że chcesz uzyskać dostęp z języka C lub moduł języka C++, należy użyć funkcji **__cplusplus —** makro preprocesora, aby określić, jaki język jest kompilowany, a następnie je określić funkcje z powiązaniem C, jeśli jest używany moduł języka C++. Jeśli używasz tej techniki i udostępniają pliki nagłówka dla biblioteki DLL, tych funkcji mogą być używane przez użytkowników C i C++ bez żadnych zmian.  
  
Poniższy kod przedstawia plik nagłówka, które mogą być używane przez aplikacje klienckie C i C++:  
  
```h  
// MyCFuncs.h  
#ifdef __cplusplus  
extern "C" {  // only need to export C interface if  
              // used by C++ source code  
#endif  
  
__declspec( dllimport ) void MyCFunc();  
__declspec( dllimport ) void AnotherCFunc();  
  
#ifdef __cplusplus  
}  
#endif  
```  
  
Jeśli musisz połączyć funkcje języka C do Twojego pliku wykonywalnego C++ i pliki nagłówków deklaracja funkcji bez użycia techniki powyżej, w pliku źródłowym C++, wykonaj następujące polecenie, aby uniemożliwić kompilatorowi dekoracji nazwy funkcji C:  
  
```cpp  
extern "C" {  
#include "MyCHeader.h"  
}  
```  
  
## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?  
  
-   [Eksportowanie z biblioteki DLL przy użyciu .def — pliki](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Eksportowanie z biblioteki DLL przy użyciu atrybutu __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Eksportowanie i importowanie przy użyciu makra AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Określić jakiej metody eksportu użyć](../build/determining-which-exporting-method-to-use.md)  
  
-   [Importowanie do aplikacji przy użyciu atrybutu __declspec(dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [Inicjowanie biblioteki DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
  
-   [Nazwy ozdobione](../build/reference/decorated-names.md)  
  
-   [Użycie zewnętrznie w celu określenia powiązania](../cpp/using-extern-to-specify-linkage.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Eksportowanie z biblioteki DLL](../build/exporting-from-a-dll.md)