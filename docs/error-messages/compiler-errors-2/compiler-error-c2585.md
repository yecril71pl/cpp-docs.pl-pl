---
title: "C2585 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2585
dev_langs: C++
helpviewer_keywords: C2585
ms.assetid: 05bb1a9c-28fb-4a88-a1b5-aea85ebdee1c
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 25df5237d2536f6f74226121cbeceba61a454390
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2585"></a>C2585 błąd kompilatora
Jawna konwersja na "type" jest niejednoznaczny  
  
 Konwersja typów można utworzyć więcej niż jeden wynik.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny  
  
1.  Konwersja z typu klasy lub struktury, oparte na dziedziczenie wielokrotne. Jeśli typ dziedziczy tej samej klasy podstawowej więcej niż raz, funkcja konwersji lub operator musi używać rozpoznawania zakresu (`::`) można określić, które z klasy dziedziczonej użyta w konwersji.  
  
2.  Operator konwersji konstruktora zdefiniowano i wprowadzania tego samego konwersji.