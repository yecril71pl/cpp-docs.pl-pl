---
title: Kompilatora (poziom 1) ostrzeżenie C4440 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4440
dev_langs:
- C++
helpviewer_keywords:
- C4440
ms.assetid: 78b9642a-a93e-401e-9d92-372f6451bc5d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 279c938a1a19fc0001923631415fee7b140399c0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276974"
---
# <a name="compiler-warning-level-1-c4440"></a>Kompilator C4440 ostrzegawcze (poziom 1)
wywoływanie definicję Konwencji wywołań z "calling_convention1" do "calling_convention2" ignorowane  
  
 Próba zmiany Konwencja wywoływania została zignorowana.  
  
 Poniższy przykład generuje C4440:  
  
```  
// C4440.cpp  
// compile with: /W1 /LD /clr  
typedef void __clrcall F();  
typedef F __cdecl *PFV;   // C4440  
```