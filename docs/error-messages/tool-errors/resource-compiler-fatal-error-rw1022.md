---
title: "Błąd krytyczny kompilatora zasobów RW1022 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- RW1022
dev_langs:
- C++
helpviewer_keywords:
- RW1022
ms.assetid: 6747c8a9-9c9b-4422-b414-0645d22092d0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a78e54496b1b0db11d8b6d6f85b5142db0d4ad6f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-fatal-error-rw1022"></a>Błąd krytyczny kompilatora zasobów RW1022
**We/Wy błąd zapisu pliku**  
  
 Kompilator zasobów nie można zapisać do pliku.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny  
  
1.  Za mało miejsca. Ilość wolnego miejsca musi wynosić co najmniej dwa razy rozmiar tworzonego pliku wykonywalnego.  
  
2.  Wolumin jest tylko do odczytu.  
  
3.  Uszkodzone sektory.  
  
4.  Nastąpiło naruszenie zasad współużytkowania.