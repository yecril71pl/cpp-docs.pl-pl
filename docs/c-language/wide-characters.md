---
title: Znaki dwubajtowe | Dokumentacja firmy Microsoft
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
helpviewer_keywords:
- wide characters
ms.assetid: 165c4a12-8ab9-45fb-9964-c55e9956194c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ab885d5d807fe81b3058d533a70cdbaa9e3e523a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="wide-characters"></a>Znaki dwubajtowe
**ANSI 3.1.3.4** wartość stała znakowa liczba całkowita, która zawiera więcej niż jeden znak lub stała znaków dwubajtowych, który zawiera więcej niż jeden znaków wielobajtowych  
  
 Zwykły znak stałej, "ab" ma wartość całkowita (int) 0x6162. W przypadku więcej niż jednego bajtu wcześniej odczytu bajtów zostaną przesunięte w lewo przez wartość **char_bit —** i następny bajt jest porównywany z niewielką ilością przy użyciu operatora Alternatywy **char_bit —** usługi bits. Liczba bajtów w stałej znaków wielobajtowych nie może przekraczać sizeof(int), która jest 4 dla docelowej 32-bitowego kodu.  
  
 Zgodnie z powyższym odczytu stała znaków wielobajtowych i jest to przekształcone na stałe znaków dwubajtowych za pośrednictwem `mbtowc` funkcji środowiska wykonawczego. Jeśli wynik nie jest prawidłową szerokich znaków stała, zgłaszany jest błąd. W każdym przypadku liczba bajtów zbadane przez `mbtowc` funkcji jest ograniczony do wartości `MB_CUR_MAX`.  
  
## <a name="see-also"></a>Zobacz też  
 [Znaki](../c-language/characters.md)