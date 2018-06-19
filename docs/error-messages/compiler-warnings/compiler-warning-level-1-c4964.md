---
title: Kompilatora (poziom 1) ostrzeżenie C4964 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4964
dev_langs:
- C++
helpviewer_keywords:
- C4964
ms.assetid: b89c9274-8a92-4b7c-aa30-3fbb1b68ac73
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 98226b2da465d2301356939273d370d76edcb64e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33290319"
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