---
title: "Przydzielanie pamięci zerowej | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- memory allocation, zero memory
- zero memory
ms.assetid: 768f2ab9-83a1-4887-8eb5-c094c18489a8
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9708f8939ff32f9320e7c8e803753e801ce9448f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="allocating-zero-memory"></a>Przydzielanie pamięci zerowej
**ANSI 4.10.3** zachowanie `calloc`, `malloc`, lub `realloc` działać, jeśli żądany rozmiar wynosi zero  
  
 `calloc`, `malloc`, I `realloc` funkcje są akceptowane wartości zerowe jako argument. Nie rzeczywiste jest rezerwowana pamięć, ale prawidłowego wskaźnika jest zwracany i blok pamięci można zmodyfikować później przy realloc.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje bibliotek](../c-language/library-functions.md)