---
title: "W tym podane nazwy plików | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 789a047e-ea38-4c99-b71d-a2ad9c81daee
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 75b9e308fec394825b3113a716ead2c93e9bb290
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="including-quoted-filenames"></a>Łącznie z nazwami plików w cudzysłowie
**ANSI 3.8.2** do obsługi nazw plików źródłowych includable w cudzysłowie  
  
 Jeśli określisz określenia ścieżki pełne, jednoznaczne dla dołączanego pliku między dwoma zestawami podwójnych cudzysłowów (""), preprocesora wyszukuje tej specyfikacji ścieżki i ignoruje standardowe katalogi.  
  
 Dla plików dołączanych określony jako [#include](../preprocessor/hash-include-directive-c-cpp.md) "Ścieżka spec", katalog wyszukiwania rozpoczyna się od katalogi pliku nadrzędnym, a następnie obejmującego katalogi plików nadrzędny. W związku z tym wyszukiwanie rozpoczyna się względem katalog zawierający plik źródłowy, w obecnie przetwarzane. Jeśli plik nadrzędny nie istnieje i nie znaleziono pliku, wyszukiwanie jest kontynuowane tak, jakby nazwa pliku są ujęte w nawiasy.  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy przetwarzania wstępnego](../c-language/preprocessing-directives.md)