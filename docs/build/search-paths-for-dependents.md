---
title: "Ścieżki wyszukiwania dla zależności | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, dependents
- dependents, NMAKE
ms.assetid: bf998e47-da74-48b5-891d-d3d8ce57264b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cf777c89c78ab844b61138c30a5a9a25ca6b91d6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="search-paths-for-dependents"></a>Przeszukuj ścieżki pod kątem zależności
Każdy zależne od ma ścieżkę wyszukiwania opcjonalne określone w następujący sposób:  
  
## <a name="syntax"></a>Składnia  
  
```  
{directory[;directory...]}dependent  
```  
  
## <a name="remarks"></a>Uwagi  
 NMAKE szuka zależnego najpierw w bieżącym katalogu, a następnie w katalogach w określonej kolejności. Makra można określić część lub całość ścieżki wyszukiwania. Umieść w nawiasach klamrowych ({}); nazwy katalogów wiele katalogów należy oddzielić średnikiem (;). Bez spacji i karty są dozwolone.  
  
## <a name="see-also"></a>Zobacz też  
 [Zależności](../build/dependents.md)