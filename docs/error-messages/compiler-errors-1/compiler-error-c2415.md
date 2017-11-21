---
title: "C2415 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2415
dev_langs: C++
helpviewer_keywords: C2415
ms.assetid: f225c913-2bea-46b1-b096-3d358ac94a15
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 68666ba203897b43fb1658525e1f342bcb923c09
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2415"></a>C2415 błąd kompilatora
Niewłaściwy argument typu  
  
 Kod operacji nie używa argumentów operacji tego typu.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny  
  
1.  Kod operacji nie obsługuje liczby argumentów operacji używane. Sprawdź podręcznika języka zestawu w celu określenia poprawnej liczby argumentów operacji.  
  
2.  Instrukcja o dodatkowe typy obsługiwanych nowszej procesor. Dostosuj [/arch (minimalna architektura Procesora)](../../build/reference/arch-minimum-cpu-architecture.md) możliwość użycia nowszego procesora.