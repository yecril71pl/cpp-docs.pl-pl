---
title: C2466 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2466
dev_langs:
- C++
helpviewer_keywords:
- C2466
ms.assetid: 75b251d1-7d0b-4a86-afca-26adedf74486
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e55e5c130b0a0454577a7155b704a18933b86198
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33224311"
---
# <a name="compiler-error-c2466"></a>C2466 błąd kompilatora
Nie można przydzielić tablicy stałego rozmiaru 0  
  
 Tablica jest przydzielona lub zadeklarowana z rozmiarem zero. Wyrażenie stałe dla rozmiaru tablicy musi być liczbą całkowitą większą niż zero. Deklaracja tablicy z zerowego indeks dolny jest dozwolony, tylko w przypadku klasy, struktury lub elementu członkowskiego typu union i tylko z rozszerzeniami firmy Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)).  
  
 Poniższy przykład generuje C2466:  
  
```  
// C2466.cpp  
// compile with: /c  
int i[0];   // C2466  
int j[1];   // OK  
char *p;  
```