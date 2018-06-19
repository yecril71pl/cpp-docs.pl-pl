---
title: Kompilatora (poziom 1) ostrzeżenie C4230 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4230
dev_langs:
- C++
helpviewer_keywords:
- C4230
ms.assetid: a4be8729-74b6-44df-a5ea-e3f45aad0f8f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf1cf97d05a794da76bc5ebd21d2b0a54f1e9eac
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33278685"
---
# <a name="compiler-warning-level-1-c4230"></a>Kompilator C4230 ostrzegawcze (poziom 1)
użyto konstrukcji przestarzałej: Modyfikatory/kwalifikatory przeplatane; Zignorowano kwalifikator  
  
 Przy użyciu kwalifikatora przed modyfikator firmy Microsoft, takich jak `__cdecl` jest przestarzała metoda.  
  
## <a name="example"></a>Przykład  
  
```  
// C4230.cpp  
// compile with: /W1 /LD  
int __cdecl const function1();   // C4230 const ignored  
```