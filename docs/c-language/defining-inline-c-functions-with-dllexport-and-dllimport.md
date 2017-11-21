---
title: "Definiowanie funkcji śródwierszowych języka C z dllexport i dllimport | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- inline functions [C++], with dllexport and dllimport
- dllimport attribute [C++], inline functions
- dllexport attribute [C++], inline functions
- dllexport attribute [C++]
ms.assetid: 41418f7c-1c11-470b-bb2e-1f8269a239f0
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 77776e174b797bd323aff0a77a2f914b8ac0b0ff
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="defining-inline-c-functions-with-dllexport-and-dllimport"></a>Definiowanie funkcji śródwierszowych języka C z dllexport i dllimport
**Dotyczące firmy Microsoft**  
  
 Można zdefiniować jako inline funkcji z `dllexport` atrybutu. W takim przypadku funkcja zawsze jest utworzone i wyeksportowane, czy każdy moduł w programie odwołuje się do funkcji. Funkcja zakłada się, że można zaimportować przez inny program.  
  
 Można również zdefiniować jako inline funkcja zadeklarowana z **dllimport** atrybutu. W takim przypadku funkcja można rozszerzyć (zgodnie ze specyfikacją opcji kompilatora /Ob (wbudowane)), ale nigdy nie miała wystąpień. W szczególności podjęcia adres zaimportowane wbudowanej funkcji jest zwracana adresu funkcji znajdującej się w bibliotece DLL. To zachowanie jest takie samo, jak pobieranie adresu innego niż inline zaimportowane funkcji.  
  
 Lokalnych danych statycznych i ciągi w funkcji śródwierszowych Obsługa tej samej tożsamości między biblioteki DLL i klienta, tak samo jak w jednym programie (czyli plik wykonywalny bez interfejsu biblioteki DLL).  
  
 Wykonuje szczególną uwagę podczas tworzenia funkcji śródwierszowych zaimportowany. Załóżmy na przykład, jeśli zaktualizujesz biblioteki DLL nie będzie używany przez klienta zmienionych wersji biblioteki dll. W celu zapewnienia ładowania poprawnej wersji biblioteki dll, Odbuduj także klienta biblioteki DLL.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Importowanie bibliotek DLL i eksportowanie funkcji](../c-language/dll-import-and-export-functions.md)