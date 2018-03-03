---
title: "Łącznie z nazwami plików w nawiasach | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 6a4e5411-c35e-48b8-90ef-b37ac324ed94
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f663de299fea33f2e104b1c70dfa1447c2840fe9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="including-bracketed-filenames"></a>Łącznie z nazwami plików w nawiasach
**ANSI 3.8.2** metody do lokalizacji plików źródłowych includable  
  
 Specyfikacji pliku ujęte w nawiasy preprocesora nie Szukaj katalogi plików nadrzędnej. Plik "nadrzędnej" jest plik, którego [#include](../preprocessor/hash-include-directive-c-cpp.md) dyrektywy w nim. Zamiast tego zaczyna się przez wyszukiwanie plików w katalogach określony na następujących kompilatora wiersza polecenia / I. Jeśli opcja nie istnieje lub nie powiedzie się, preprocesora użycie zmiennej środowiskowej INCLUDE można znaleźć żadnych plików dołączanych w nawiasy. Zmiennej środowiskowej INCLUDE mogą zawierać wiele ścieżek rozdzielonych średnikami (**;**). Jeśli więcej niż jeden katalog jest wyświetlany jako część opcji /I lub w zmiennej środowiskowej INCLUDE, preprocesora przeszukuje je w kolejności ich występowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy przetwarzania wstępnego](../c-language/preprocessing-directives.md)