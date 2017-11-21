---
title: "C2414 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2414
dev_langs: C++
helpviewer_keywords: C2414
ms.assetid: bbe94e03-862e-4990-b15e-544ae464727d
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f3b532fdb8448f616916adcaf047dc83923f62c0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2414"></a>C2414 błąd kompilatora
Niedozwolona liczba operandów  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny  
  
1.  Kod operacji nie obsługuje liczby argumentów operacji używane. Sprawdź podręcznika języka zestawu w celu określenia poprawnej liczby argumentów operacji.  
  
2.  Procesor nowszej obsługuje instrukcji z różną liczbą argumentów operacji. Dostosuj [/arch (minimalna architektura Procesora)](../../build/reference/arch-minimum-cpu-architecture.md) możliwość użycia nowszego procesora.