---
title: "Definiowanie funkcji śródwierszowych języka C++ z dllexport i dllimport | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- inline functions [C++], defining
- functions [C++], defining inline
- dllimport attribute [C++], inline functions
- dllexport attribute [C++], inline functions
ms.assetid: 3b48678b-e7b8-4eda-bb46-b5d34dcf7817
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 125bd894c5448c20948da04b6d7acbe959cc2c9f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="defining-inline-c-functions-with-dllexport-and-dllimport"></a>Definiowanie funkcji śródwierszowych języka C++ z dllexport i dllimport
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Można zdefiniować jako inline funkcji z `dllexport` atrybutu. W takim przypadku funkcja zawsze jest utworzone i wyeksportowane, czy każdy moduł w programie odwołuje się do funkcji. Funkcja zakłada się, że można zaimportować przez inny program.  
  
 Można również zdefiniować jako inline funkcja zadeklarowana z **dllimport** atrybutu. W takim przypadku funkcji może być rozwinięty (może ulec specyfikacje /Ob), ale nigdy nie miała wystąpień. W szczególności podjęcia adres zaimportowane wbudowanej funkcji jest zwracana adresu funkcji znajdującej się w bibliotece DLL. To zachowanie jest takie samo, jak pobieranie adresu innego niż inline zaimportowane funkcji.  
  
 Te reguły dotyczą wbudowane funkcje, których definicje są wyświetlane w definicji klasy. Ponadto lokalnych danych statycznych i ciągi w funkcji śródwierszowych Obsługa tej samej tożsamości między biblioteki DLL i klienta, tak samo jak w jednym programie (czyli plik wykonywalny bez interfejsu biblioteki DLL).  
  
 Wykonuje szczególną uwagę podczas tworzenia funkcji śródwierszowych zaimportowany. Załóżmy na przykład, jeśli zaktualizujesz biblioteki DLL nie będzie używany przez klienta zmienionych wersji biblioteki dll. W celu zapewnienia ładowania poprawnej wersji biblioteki dll, Odbuduj także klienta biblioteki DLL.  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [dllexport i dllimport](../cpp/dllexport-dllimport.md)