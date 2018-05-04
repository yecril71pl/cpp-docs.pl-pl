---
title: Importowanie i eksportowanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], importing
- exporting DLLs [C++]
- importing DLLs [C++]
- DLLs [C++], exporting from
- __declspec(dllimport) keyword [C++]
ms.assetid: 7c44c2aa-2117-4cec-9615-a65bfd3f8f7b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ee3ffe33dbb99f1f9b4124e2695d2e56dbe5544
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="importing-and-exporting"></a>Importowanie i eksportowanie
Możesz zaimportować symbole publiczne do aplikacji lub eksportowanie funkcji z biblioteki DLL przy użyciu dwóch metod:  
  
-   Podczas tworzenia biblioteki DLL przy użyciu pliku modułu definicji (.def)  
  
-   Użyj słowa kluczowe **__declspec(dllimport)** lub **__declspec(dllexport)** w definicji funkcji w głównej aplikacji  
  
## <a name="using-a-def-file"></a>Używany plik .def  
 Plik definicji modułu (.def) to plik tekstowy zawierający co najmniej jeden moduł instrukcje opisujących różne atrybuty biblioteki dll. Jeśli nie używasz **__declspec(dllimport)** lub **__declspec(dllexport)** wyeksportować funkcji DLL, plik .def wymaga biblioteki DLL.  
  
 Można użyć .def — pliki do [importowanie do aplikacji](../build/importing-using-def-files.md) lub [eksportowanie z biblioteki DLL](../build/exporting-from-a-dll-using-def-files.md).  
  
## <a name="using-declspec"></a>Przy użyciu __declspec  
 Visual C++ używa **__declspec(dllimport)** i **__declspec(dllexport)** zastąpić **__export** — słowo kluczowe wcześniej używany w 16-bitowych wersjach Visual C++.  
  
 Nie trzeba używać **__declspec(dllimport)** swój kod, aby skompilować poprawnie, ale w ten sposób umożliwia kompilatorowi generowanie kodu lepiej. Kompilator jest w stanie wygenerować kodu lepsze, ponieważ można określić, czy funkcję istnieje w bibliotece DLL lub nie, który umożliwia kompilatorowi tworzenia kodu z pominięciem poziom pośredni, które zwykle będą obecne w wywołaniu funkcji, które przekroczeniu granic DLL. Jednak należy użyć **__declspec(dllimport)** do zaimportowania zmienne używane w bibliotece DLL.  
  
 Z sekcji .def prawidłowego pliku EKSPORTÓW **__declspec(dllexport)** nie jest wymagana. **__declspec(dllexport)** został dodany do umożliwiają łatwe do wyeksportowania funkcji z pliku .exe lub .dll bez użycia pliku .def.  
  
 Format przenośnej plikiem wykonywalnym środowiska Win32 jest przeznaczona do zminimalizować liczbę stron, które muszą być dotknięciu ustalenie importów. Aby to zrobić, umieszcza w jednym miejscu o nazwie tabeli Adres zaimportować wszystkie adresy importu dla dowolnego programu. Dzięki temu można zmodyfikować jedną lub dwie strony podczas uzyskiwania dostępu do tych importuje moduł ładujący.  
  
## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?  
  
-   [Importowanie do aplikacji](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [Eksportowanie z biblioteki DLL](../build/exporting-from-a-dll.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteki DLL w programie Visual C++](../build/dlls-in-visual-cpp.md)