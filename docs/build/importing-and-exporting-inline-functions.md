---
title: "Importowanie i eksportowanie funkcji śródwierszowych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- exporting functions [C++], inline functions
- inline functions [C++], importing
- DLLs [C++], importing
- importing functions [C++]
- DLLs [C++], exporting from
- importing inline functions [C++]
- inline functions [C++], exporting
- functions [C++], importing
- functions [C++], exporting
ms.assetid: 89f488f8-b078-40fe-afd7-80bd7840057b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a6f8d159a1537cdfee02d45805632ba9ad4afa7e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="importing-and-exporting-inline-functions"></a>Importowanie i eksportowanie funkcji śródwierszowych
Funkcje importowanych można zdefiniować jako śródwierszowej. Efekt około jest taka sama jak definiowanie w tekście standardowa funkcja; wywołania funkcji są rozwijane do kodu wbudowanego, podobnie jak w makrze. Jest to przydatne głównie sposób obsługi języka C++ klasy w bibliotece DLL tym miejscu może niektóre z ich funkcji w celu zwiększenia wydajności.  
  
 Jedna funkcja importowanych wbudowanej funkcji jest wykonanie adresu w języku C++. Kompilator zwraca adres kopię funkcji wbudowanej znajdującej się w bibliotece DLL. Inna funkcja funkcji śródwierszowych importowany jest zainicjować lokalnych danych statycznych funkcji importowane, w przeciwieństwie do importowanych danych globalnych.  
  
> [!CAUTION]
>  Szczególną uwagę należy postępować importowane zapewnianie funkcji śródwierszowych ponieważ mogą utworzyć konfliktów wersji. Funkcja wbudowana pobiera rozwinięty w kodzie aplikacji; w związku z tym jeśli później ponownego zapisywania funkcji go nie zostanie zaktualizowany, chyba że sama aplikacja jest ponownie kompilowana. (Zazwyczaj funkcji DLL może zostać zaktualizowana w bez odbudowywania aplikacje, które z nich korzystają.)  
  
## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?  
  
-   [Eksportowanie z biblioteki DLL](../build/exporting-from-a-dll.md)  
  
-   [Eksportowanie z biblioteki DLL przy użyciu. Pliki DEF](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Eksportowanie z biblioteki DLL przy użyciu atrybutu __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Eksportowanie i importowanie przy użyciu makra AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Eksportowanie funkcji języka C++ do użycia w plikach wykonywalnych języka C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Określić jakiej metody eksportu użyć](../build/determining-which-exporting-method-to-use.md)  
  
-   [Importowanie do aplikacji przy użyciu atrybutu __declspec(dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Importowanie i eksportowanie](../build/importing-and-exporting.md)