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
ms.openlocfilehash: 561359afcd9cf694369bd1addb4f641a33a3f989
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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