---
title: C4394 ostrzeżenia kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4394
dev_langs:
- C++
helpviewer_keywords:
- C4394
ms.assetid: 5de94de0-17e3-4e7c-92f4-5c3c1b825120
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 05535621443770a2b414f1c4312efbc46e6be858
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-c4394"></a>C4394 ostrzeżenia kompilatora
"Funkcja": symbol per-appdomain nie powinien być oznaczony przez __declspec(dllexport)  
  
 Funkcja oznaczona atrybutem [elementu appdomain](../../cpp/appdomain.md) `__declspec` modyfikator jest skompilowane do MSIL (nie do natywnego) i tabele eksportu ([wyeksportować](../../windows/export.md) `__declspec` modyfikator) nie są obsługiwane dla funkcji zarządzanych.  
  
 Można zadeklarować zarządzanego funkcji, aby mieć powszechnej dostępności. Aby uzyskać więcej informacji, zobacz [wpisz widoczność](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) i [widoczności elementów członkowskich](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility).  
  
 C4394 jest zawsze wystawione jako błąd.  Możesz wyłączyć to ostrzeżenie o `#pragma warning` lub **/wd**; zobacz [ostrzeżenie](../../preprocessor/warning.md) lub [/w, /W0, /W1, /W2, /W3, / W4, /w1, /w2, /w3, / W4, / Wall, /wd, / możemy /wo, /Wv, wx (poziom ostrzegawczy)](../../build/reference/compiler-option-warning-level.md)Aby uzyskać więcej informacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4394.  
  
```  
// C4394.cpp  
// compile with: /clr /c  
__declspec(dllexport) __declspec(appdomain) int g1 = 0;   // C4394  
__declspec(dllexport) int g2 = 0;   // OK  
```