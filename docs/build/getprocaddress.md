---
title: GetProcAddress | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: GetProcAddress
dev_langs: C++
helpviewer_keywords:
- DLLs [C++], GetProcAddress
- ordinal exports [C++]
- GetProcAddress method
ms.assetid: 48d14ae0-47ea-4c5d-96b1-2c158f1a26af
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2bc32c5f6b6ae4ee80c69dff028f05d2b334d920
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="getprocaddress"></a>GetProcAddress
Procesy jawnie łączenia wywołanie biblioteki DLL [GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212) do uzyskiwania adresów wyeksportowanej funkcji w bibliotece DLL. Wywoływanie funkcji DLL za pomocą wskaźnika funkcji zwrócony. **GetProcAddress** przyjmuje jako parametry uchwytu modułu DLL (zwrócony przez **LoadLibrary**, `AfxLoadLibrary`, lub **GetModuleHandle**) i pobiera nazwę funkcji można chcesz wywołania lub funkcji eksportu porządkowych.  
  
 Ponieważ to wywołanie funkcji DLL za pomocą wskaźnika i nie ma typu kompilacji sprawdzania, upewnij się, parametry funkcji są poprawne, tak aby nie overstep pamięci przydzielony na stosie i spowodować naruszenie zasad dostępu. Jednym ze sposobów pomaga zapewnić bezpieczeństwo typów jest przyjrzeć się prototypy funkcji wyeksportowanej funkcji i Utwórz pasujące definicje typów dla wskaźników funkcji. Na przykład:  
  
```  
typedef UINT (CALLBACK* LPFNDLLFUNC1)(DWORD,UINT);  
...  
  
HINSTANCE hDLL;               // Handle to DLL  
LPFNDLLFUNC1 lpfnDllFunc1;    // Function pointer  
DWORD dwParam1;  
UINT  uParam2, uReturnVal;  
  
hDLL = LoadLibrary("MyDLL");  
if (hDLL != NULL)  
{  
   lpfnDllFunc1 = (LPFNDLLFUNC1)GetProcAddress(hDLL,  
                                           "DLLFunc1");  
   if (!lpfnDllFunc1)  
   {  
      // handle the error  
      FreeLibrary(hDLL);  
      return SOME_ERROR_CODE;  
   }  
   else  
   {  
      // call the function  
      uReturnVal = lpfnDllFunc1(dwParam1, uParam2);  
   }  
}  
```  
  
 Jak określić podczas wywoływania funkcji **GetProcAddress** zależy od sposobu Biblioteka DLL została skompilowana.  
  
 Tylko i można uzyskać numer porządkowy eksportu Jeśli biblioteki DLL, połączenie jest ustanawiane jest zbudowany z pliku definicji (.def) moduł porządkowe wymienione z funkcjami w **EKSPORTÓW** sekcji plik .def DLL. Wywoływanie **GetProcAddress** numer, a nie nazwą funkcji eksportu jest nieco większą biblioteki DLL ma wiele funkcji wyeksportowanej ponieważ porządkowe eksportu tworzą indeksy do biblioteki DLL Eksportowanie tabeli. Z numeru porządkowego eksportu **GetProcAddress** można zlokalizować funkcji bezpośrednio w przeciwieństwie porównanie nazwy określonej nazwy funkcji w tabeli eksportu biblioteki DLL. Jednak należy wywołać **GetProcAddress** z numeru porządkowego eksportu tylko wtedy, gdy mają kontrolę nad przypisywanie porządkowe wyeksportowanej funkcji w pliku .def.  
  
## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?  
  
-   [Jak połączyć niejawnie z biblioteki DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)  
  
-   [Określić jakiej metody łączenia użyć](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
  
-   [LoadLibrary i AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)  
  
-   [FreeLibrary](http://msdn.microsoft.com/library/windows/desktop/ms683152)  
  
-   [Eksportowanie z biblioteki DLL przy użyciu plików DEF](../build/exporting-from-a-dll-using-def-files.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteki DLL w programie Visual C++](../build/dlls-in-visual-cpp.md)