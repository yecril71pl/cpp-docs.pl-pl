---
title: Eksportowanie z biblioteki DLL | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- exporting DLLs [C++], about exporting from DLLs
- exporting functions [C++], DLLs (exporting from)
- exporting DLLs [C++]
- DLLs [C++], exporting from
- DLL exports [C++]
- functions [C++], exporting
- exports table [C++]
ms.assetid: a08f86c4-5996-460b-ae54-da2b764045f0
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 64571a0f648c0e33635990d9ca57744877429049
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="exporting-from-a-dll"></a>Eksportowanie z biblioteki DLL  
  
Plik DLL jest bardzo podobny do pliku .exe, z jedną istotną różnicą — plik DLL zawiera tabelę eksportu. Tabela eksportów zawiera nazwę każdej funkcji, które eksportuje biblioteki DLL do innych plików wykonywalnych. Te funkcje są punktów wejścia w bibliotece DLL; tylko funkcje w tabeli eksportu są dostępne przez inne pliki wykonywalne. Jakichkolwiek innych funkcji w bibliotece DLL są prywatne do pliku DLL. Można wyświetlić tabeli eksporty biblioteki DLL przy użyciu [DUMPBIN](../build/reference/dumpbin-reference.md) narzędzie z opcją /EXPORTS.  
  
 Funkcje można wyeksportować z biblioteki DLL przy użyciu dwóch metod:  
  
-   Utwórz plik definicji (.def) modułu i użyć pliku .def podczas tworzenia biblioteki DLL. Tej metody należy użyć, jeśli chcesz [eksportowanie funkcji z biblioteki DLL według liczby porządkowej, a nie nazwy](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).  
  
-   Użyj słowa kluczowego **__declspec(dllexport)** w definicji funkcji.  
  
 Podczas eksportowania funkcji z jednej z metod, upewnij się użyć [__stdcall](../cpp/stdcall.md) konwencji wywoływania.  
  
## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?  
  
-   [Eksportowanie z biblioteki DLL przy użyciu .def — pliki](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Eksportowanie z biblioteki DLL przy użyciu atrybutu __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Eksportowanie i importowanie przy użyciu makra AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Eksportowanie funkcji języka C++ do użycia w plikach wykonywalnych języka C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Eksportowanie funkcji języka C do użycia w plikach wykonywalnych języka C lub języka C++](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [Eksportowanie funkcji z biblioteki DLL według liczby porządkowej, a nie według nazwy](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)  
  
-   [Określić jakiej metody eksportu użyć](../build/determining-which-exporting-method-to-use.md)  
  
-   [Określić jakiej metody łączenia użyć](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)  
  
-   [Inicjowanie biblioteki DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
  
-   [Importowanie do aplikacji](../build/importing-into-an-application.md)  
  
-   [Importowanie i eksportowanie funkcji śródwierszowych](../build/importing-and-exporting-inline-functions.md)  
  
-   [Importy wzajemne](../build/mutual-imports.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Importowanie i eksportowanie](../build/importing-and-exporting.md)