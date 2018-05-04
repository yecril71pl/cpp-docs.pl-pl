---
title: Znaki dwubajtowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- wide characters
ms.assetid: 165c4a12-8ab9-45fb-9964-c55e9956194c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf20b58ad9343f1a90f07a7f4c07bccd397a5888
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="wide-characters"></a>Znaki dwubajtowe
**ANSI 3.1.3.4** wartość stała znakowa liczba całkowita, która zawiera więcej niż jeden znak lub stała znaków dwubajtowych, który zawiera więcej niż jeden znaków wielobajtowych  
  
 Zwykły znak stałej, "ab" ma wartość całkowita (int) 0x6162. W przypadku więcej niż jednego bajtu wcześniej odczytu bajtów zostaną przesunięte w lewo przez wartość **char_bit —** i następny bajt jest porównywany z niewielką ilością przy użyciu operatora Alternatywy **char_bit —** usługi bits. Liczba bajtów w stałej znaków wielobajtowych nie może przekraczać sizeof(int), która jest 4 dla docelowej 32-bitowego kodu.  
  
 Zgodnie z powyższym odczytu stała znaków wielobajtowych i jest to przekształcone na stałe znaków dwubajtowych za pośrednictwem `mbtowc` funkcji środowiska wykonawczego. Jeśli wynik nie jest prawidłową szerokich znaków stała, zgłaszany jest błąd. W każdym przypadku liczba bajtów zbadane przez `mbtowc` funkcji jest ograniczony do wartości `MB_CUR_MAX`.  
  
## <a name="see-also"></a>Zobacz też  
 [Znaki](../c-language/characters.md)