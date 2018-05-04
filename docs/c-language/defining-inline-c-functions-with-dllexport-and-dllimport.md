---
title: Definiowanie funkcji śródwierszowych języka C z dllexport i dllimport | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- inline functions [C++], with dllexport and dllimport
- dllimport attribute [C++], inline functions
- dllexport attribute [C++], inline functions
- dllexport attribute [C++]
ms.assetid: 41418f7c-1c11-470b-bb2e-1f8269a239f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 58ca4ab6fdfe06dec6d790db3135e42a6eeb39d8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="defining-inline-c-functions-with-dllexport-and-dllimport"></a>Definiowanie funkcji śródwierszowych języka C z dllexport i dllimport
**Microsoft Specific**  
  
 Można zdefiniować jako inline funkcji z `dllexport` atrybutu. W takim przypadku funkcja zawsze jest utworzone i wyeksportowane, czy każdy moduł w programie odwołuje się do funkcji. Funkcja zakłada się, że można zaimportować przez inny program.  
  
 Można również zdefiniować jako inline funkcja zadeklarowana z **dllimport** atrybutu. W takim przypadku funkcja można rozszerzyć (zgodnie ze specyfikacją opcji kompilatora /Ob (wbudowane)), ale nigdy nie miała wystąpień. W szczególności podjęcia adres zaimportowane wbudowanej funkcji jest zwracana adresu funkcji znajdującej się w bibliotece DLL. To zachowanie jest takie samo, jak pobieranie adresu innego niż inline zaimportowane funkcji.  
  
 Lokalnych danych statycznych i ciągi w funkcji śródwierszowych Obsługa tej samej tożsamości między biblioteki DLL i klienta, tak samo jak w jednym programie (czyli plik wykonywalny bez interfejsu biblioteki DLL).  
  
 Wykonuje szczególną uwagę podczas tworzenia funkcji śródwierszowych zaimportowany. Załóżmy na przykład, jeśli zaktualizujesz biblioteki DLL nie będzie używany przez klienta zmienionych wersji biblioteki dll. W celu zapewnienia ładowania poprawnej wersji biblioteki dll, Odbuduj także klienta biblioteki DLL.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Importowanie bibliotek DLL i eksportowanie funkcji](../c-language/dll-import-and-export-functions.md)