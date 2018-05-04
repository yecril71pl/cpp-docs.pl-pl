---
title: Ścieżki wyszukiwania dla zależności | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, dependents
- dependents, NMAKE
ms.assetid: bf998e47-da74-48b5-891d-d3d8ce57264b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 577fc7e44bfff35cf7efdcff20dc4cdca1c7001e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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