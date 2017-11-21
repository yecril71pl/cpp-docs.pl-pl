---
title: "Importowanie do aplikacji przy użyciu atrybutu __declspec(dllimport) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- __declspec
- dllimport
dev_langs: C++
helpviewer_keywords:
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: edb4da4e-f83a-44cf-a668-9239d49dbe42
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4f16c9f5c96712c311928e0389fec0a1ce1f0dca
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="importing-into-an-application-using-declspecdllimport"></a>Importowanie do aplikacji przy użyciu atrybutu __declspec(dllimport)
Program, który używa publicznego symboli zdefiniowanych przez bibliotekę DLL jest nazywany ich importowania. Po utworzeniu pliki nagłówkowe dla aplikacji, które korzystają z bibliotek DLL do skompilowania z użyciem, użyj **__declspec(dllimport)** w deklaracjach symbole publiczne. Słowo kluczowe **__declspec(dllimport)** działa, czy możesz wyeksportować z .def — pliki lub **__declspec(dllexport)** — słowo kluczowe.  
  
 Aby zwiększyć czytelność kodu, zdefiniuj makro **__declspec(dllimport)** , a następnie użyć do zadeklarowania każdego zaimportowanego symbol makra:  
  
```  
#define DllImport   __declspec( dllimport )  
  
DllImport int  j;  
DllImport void func();  
```  
  
 Przy użyciu **__declspec(dllimport)** jest opcjonalna w deklaracjach funkcji, ale kompilator tworzy kodu bardziej wydajne użycie słowa kluczowego. Jednak należy użyć **__declspec(dllimport)** importowania pliku wykonywalnego, dostęp do danych publicznych symbole DLL i obiektów. Należy zauważyć, że użytkownicy biblioteki DLL nadal do połączenia z biblioteką importu.  
  
 Można użyć tego samego pliku nagłówka dla biblioteki DLL i aplikacji klienckiej. Aby to zrobić, Użyj specjalnych symbol preprocesora, która wskazuje, czy tworzenie biblioteki DLL lub tworzenie aplikacji klienckich. Na przykład:  
  
```  
#ifdef _EXPORTING  
   #define CLASS_DECLSPEC    __declspec(dllexport)  
#else  
   #define CLASS_DECLSPEC    __declspec(dllimport)  
#endif  
  
class CLASS_DECLSPEC CExampleA : public CObject  
{ ... class definition ... };  
```  
  
## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?  
  
-   [Inicjowanie biblioteki DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
  
-   [Importowanie i eksportowanie funkcji śródwierszowych](../build/importing-and-exporting-inline-functions.md)  
  
-   [Importy wzajemne](../build/mutual-imports.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Importowanie do aplikacji](../build/importing-into-an-application.md)