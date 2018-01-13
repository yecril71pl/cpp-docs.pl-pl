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
ms.workload: cplusplus
ms.openlocfilehash: f6093db4ac8e0c88dfe6e4b5a5463e5ee8d24349
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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