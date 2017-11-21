---
title: "Typy całkowite o rozmiarze C | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: sized integer types
ms.assetid: 0d6199b4-d0ab-4e8c-a769-785f5afb92eb
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 101c8facb8871d814d1a1ea05c2856d3105a8bfc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="c-sized-integer-types"></a>Typy liczb całkowitych o rozmiarze C
**Dotyczące firmy Microsoft**  
  
 Obsługuje funkcje Microsoft C dla typy całkowite o określonym rozmiarze. 8 - 16-, 32- i 64-bitową liczbę całkowitą zmienne można zadeklarować przy użyciu __int *n*  wpisz specyfikator, gdzie  *n*  w bitach zmienna całkowitoliczbowa rozmiar. Wartość  *n*  8, 16, 32 lub 64. Poniższy przykład deklaruje jedną zmienną dla każdego z czterech typów liczb całkowitych o rozmiarze:  
  
```  
__int8 nSmall;      // Declares 8-bit integer  
__int16 nMedium;    // Declares 16-bit integer  
__int32 nLarge;     // Declares 32-bit integer  
__int64 nHuge;      // Declares 64-bit integer  
```  
  
 Pierwsze trzy typy liczb całkowitych o rozmiarze są synonimy dla typów ANSI, które mają taki sam rozmiar i ułatwia pisanie kodu przenośny, który zachowuje się tak samo na wielu platformach. Należy pamiętać, że typ danych __int8 synonimem Typ char \__int16 jest synonimem krótkie, typ i \__int32 jest synonimem typu int. \__Int64 typu nie ma odpowiednika równoważne ANSI.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Magazyn typów podstawowych](../c-language/storage-of-basic-types.md)