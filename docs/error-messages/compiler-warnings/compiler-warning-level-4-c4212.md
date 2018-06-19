---
title: Kompilatora (poziom 4) ostrzeżenie C4212 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4212
dev_langs:
- C++
helpviewer_keywords:
- C4212
ms.assetid: df781ea1-182d-4f9f-9a31-55b6ce80c711
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb70cf045a1cc563e4eb009ed00ffe82be812b0b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292006"
---
# <a name="compiler-warning-level-4-c4212"></a>Kompilator C4212 ostrzegawcze (poziom 4)
użyto niestandardowego rozszerzenia: deklaracji funkcji użyto wielokropka  
  
 Prototyp funkcji ma zmienną liczbę argumentów. Nie ma definicji funkcji.  
  
 Poniższy przykład generuje C4212:  
  
```  
// C4212.c  
// compile with: /W4 /Ze /c  
void f(int , ...);  
void f(int i, int j) {}  
```