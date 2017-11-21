---
title: "Kompilatora (poziom 1) ostrzeżenie C4964 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4964
dev_langs: C++
helpviewer_keywords: C4964
ms.assetid: b89c9274-8a92-4b7c-aa30-3fbb1b68ac73
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 272e9dec1a0f587d4e381e482f7bbf089cc8e4c9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4964"></a>Kompilator C4964 ostrzegawcze (poziom 1)
Optymalizacja nie określono żadnych opcji; informacje o profilu nie będą zbierane.  
  
 [/GL](../../build/reference/gl-whole-program-optimization.md) i [opcję/LTCG](../../build/reference/ltcg-link-time-code-generation.md) zostały określone, ale brak optymalizacji zażądał, dzięki czemu będą generowane żadne pliki .pgc i, w związku z tym profilowana Optymalizacja została nie będzie możliwe.  
  
 Jeśli chcesz, aby pliki .pgc do wygenerowania po uruchomieniu aplikacji, określ jedną z [/O](../../build/reference/o-options-optimize-code.md) — opcje kompilatora.  
  
 Poniższy przykład generuje C4964:  
  
```  
// C4964.cpp  
// compile with: /W1 /GL /link /ltcg:pgi  
// C4964 expected  
// Add /O2, for example, to the command line to resolve this warning.  
int main() {  
   int i;  
}  
```