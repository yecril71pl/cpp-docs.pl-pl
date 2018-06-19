---
title: Kompilatora (poziom 1) ostrzeżenie C4052 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4052
dev_langs:
- C++
helpviewer_keywords:
- C4052
ms.assetid: f9955421-16ab-46e5-8f9d-bf1639a519ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5c937e602f14789419f6b124034503c127f6dc2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33271194"
---
# <a name="compiler-warning-level-1-c4052"></a>Kompilator C4052 ostrzegawcze (poziom 1)
deklaracje funkcji różne; jeden z nich zawiera zmienne argumenty  
  
 Jedną deklarację funkcji nie zawiera zmiennych argumentów. Jest on ignorowany.  
  
 Poniższy przykład generuje C4052:  
  
```  
// C4052.c  
// compile with: /W4 /c  
int f();  
int f(int i, ...);   // C4052  
```