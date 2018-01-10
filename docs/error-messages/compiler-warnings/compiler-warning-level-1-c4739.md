---
title: "Kompilatora (poziom 1) ostrzeżenie C4739 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4739
dev_langs: C++
helpviewer_keywords: C4739
ms.assetid: 600873b3-7c85-4cd4-944e-cd8e01bfcbb0
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d11002afb2eac0c7f9c6971bca3610463eed0d55
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4739"></a>Kompilator C4739 ostrzegawcze (poziom 1)
Odwołanie do zmiennej "var" przekracza jego miejsce do magazynowania  
  
 Wartość została przypisana do zmiennej, ale wartość jest większa niż rozmiar zmiennej. Pamięć zostanie zapisany poza zmiennej lokalizacji pamięci i możliwa jest utrata danych.  
  
 Aby usunąć to ostrzeżenie, tylko przypisać wartości do zmiennej, którego rozmiar może obsłużyć wartość.  
  
 Poniższy przykład generuje C4739:  
  
```  
// C4739.cpp  
// compile with: /RTCs /Zi /W1 /c  
char *pc;  
int main() {  
   char c;  
   *(int *)&c = 1;   // C4739  
  
   // OK  
   *(char *)&c = 1;  
}  
```