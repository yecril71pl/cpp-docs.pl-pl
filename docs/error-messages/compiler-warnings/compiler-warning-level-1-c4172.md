---
title: "Kompilatora (poziom 1) ostrzeżenie C4172 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4172
dev_langs: C++
helpviewer_keywords: C4172
ms.assetid: a8d2bf65-d8b1-4fe3-8340-a223d7e7fde6
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3cda1f5c578be76bbe98b60d014a70e970fcc2d0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4172"></a>Kompilator C4172 ostrzegawcze (poziom 1)
zwracanie adresu lokalnej zmiennej lub tymczasowej  
  
 Funkcja zwraca adres obiektu lokalnej zmiennej lub tymczasowej. Zmienne lokalne i obiekty tymczasowe zostaną zniszczone po powrocie z funkcji, adres, zwracana jest nieprawidłowy.  
  
 Zmodyfikowanie funkcji, dzięki czemu nie zwróci adresu lokalnego obiektu.  
  
 Poniższy przykład generuje C4172:  
  
```  
// C4172.cpp  
// compile with: /W1 /LD  
float f = 10;  
  
const double& bar() {  
// try the following line instead  
// const float& bar() {  
   return f;   // C4172  
}  
```