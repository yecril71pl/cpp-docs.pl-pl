---
title: Eksportowanie funkcji języka C++ do użycia w plikach wykonywalnych języka C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], C++ functions in C executables
- exporting DLLs [C++], C++ functions in C executables
- exporting functions [C++], C++ functions in C executables
- functions [C++], exporting
ms.assetid: 80b9e982-f52d-4312-a891-f73cc69f3c2b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cf5f348675752ff9c0b548693c442812fa6be697
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367589"
---
# <a name="exporting-c-functions-for-use-in-c-language-executables"></a>Eksportowanie funkcji języka C++ do użycia w plikach wykonywalnych języka C  
  
Jeśli masz funkcji w bibliotece DLL napisana w języku C++, że chcesz uzyskać dostęp z modułu języka C, należy zadeklarować tych funkcji z powiązaniem C zamiast połączenie C++. Inaczej, kompilator języka C++ używa C++ bezpieczne nazewnictwa (nazwij dekorację) i C++ wywoływanie Konwencji, które mogą być trudne do wywołania z C.  
  
Aby określić powiązanie C, określ `extern "C"` dla Twojego deklaracje funkcji. Na przykład:  
  
```  
extern "C" __declspec( dllexport ) int MyFunc(long parm1);  
```  
  
## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?  
  
-   [Eksportowanie z biblioteki DLL przy użyciu .def — pliki](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Eksportowanie z biblioteki DLL przy użyciu atrybutu __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Eksportowanie i importowanie przy użyciu makra AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Eksportowanie funkcji języka C do użycia w plikach wykonywalnych języka C lub języka C++](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [Określić jakiej metody eksportu użyć](../build/determining-which-exporting-method-to-use.md)  
  
-   [Importowanie do aplikacji przy użyciu atrybutu __declspec(dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [Inicjowanie biblioteki DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
  
-   [Nazwy ozdobione](../build/reference/decorated-names.md)  
  
-   [Użycie zewnętrznie w celu określenia powiązania](../cpp/using-extern-to-specify-linkage.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Eksportowanie z biblioteki DLL](../build/exporting-from-a-dll.md)