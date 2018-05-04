---
title: Importowanie do aplikacji przy użyciu atrybutu __declspec(dllimport) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- __declspec
- dllimport
dev_langs:
- C++
helpviewer_keywords:
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: edb4da4e-f83a-44cf-a668-9239d49dbe42
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82974ec688fbe688c98188c2e99a54462da81165
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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