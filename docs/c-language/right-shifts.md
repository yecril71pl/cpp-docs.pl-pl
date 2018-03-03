---
title: "Kliknij prawym przyciskiem myszy przesuwa się | Dokumentacja firmy Microsoft"
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
ms.assetid: c878e97d-ea3c-4c6b-90a8-b1b24b2d5b19
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 307cf91bf86f2912ad6cafa7e89f48e614c3865a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="right-shifts"></a>Przesunięcia w prawo
Wynik przesunięcia w prawo o wartości ujemnej podpisany typ całkowity  
  
 Przesunięcie w prawo wartości ujemnej daje połowa wartość bezwzględna, zaokrąglona w dół. Na przykład podpisem `short` wartość -253 (0xFF03 szesnastkowych, binary 11111111 00000011) przesunięte daje prawo o jeden bit -127 (0xFF81 szesnastkowych, binary 11111111 10000001). Dodatnia 253 przesunięte daje prawo +126.  
  
 Przesunięcia w prawo zachować bitu znaku z podpisanych typów całkowitych. Kiedy całkowita przewiduje się po prawej, najbardziej znaczącego bitu pozostaje ustawione. Na przykład, jeśli jest zalogowany 0xF0000000 `int`, 0xF8000000 tworzy przesunięcia w prawo. Przesunięcie ujemny `int` prawo 32 razy tworzy 0xFFFFFFFF.  
  
 Gdy całkowitą bez znaku przewiduje się po prawej, najbardziej znaczącego bitu jest wyczyszczone. Na przykład jeśli 0xF000 nie jest podpisany, wynik jest 0x7800. Przesunięcie `unsigned` lub dodatnią `int` prawo 32 razy tworzy 0x00000000.  
  
## <a name="see-also"></a>Zobacz też  
 [Liczby całkowite](../c-language/integers.md)