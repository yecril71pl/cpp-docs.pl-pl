---
title: "C3389 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3389
dev_langs: C++
helpviewer_keywords: C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bd88753553d2bad1cb9253cfe709e7627c4b01ba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3389"></a>C3389 błąd kompilatora
__declspec(keyword) nie może być użyty z/CLR: pure lub/CLR: Safe  
  
 **/CLR: pure** i **/CLR: Safe** — opcje kompilatora zostały uznane za przestarzałe w programie Visual Studio 2015.  
  
 A [__declspec](../../cpp/declspec.md) oznacza modyfikator używane na stan procesu.  [/ CLR: pure](../../build/reference/clr-common-language-runtime-compilation.md) oznacza na [elementu appdomain](../../cpp/appdomain.md) stanu.  Tak, deklarowanie zmiennej o `keyword` **__declspec** modyfikator i kompilowania przy użyciu **/CLR: pure** jest niedozwolone.  
  
 Poniższy przykład generuje C3389:  
  
```  
// C3389.cpp  
// compile with: /clr:pure /c  
__declspec(dllexport) int g2 = 0;   // C3389  
```