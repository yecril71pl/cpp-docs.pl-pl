---
title: "C2393 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2393
dev_langs: C++
helpviewer_keywords: C2393
ms.assetid: 4bd95728-e813-4ce8-844a-c6ebe235ca82
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a2c4f8d31fb6ddb6eaa9472dc7537edbcdc29054
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2393"></a>C2393 błąd kompilatora
"symbol": symbol per-appdomain nie może zostać alokowany w segmencie "segmentu"  
  
 **/CLR: pure** i **/CLR: Safe** — opcje kompilatora zostały uznane za przestarzałe w programie Visual Studio 2015.  
  
 Korzystanie z [elementu appdomain](../../cpp/appdomain.md) zmienne oznacza, że kompilacja z **/CLR: pure** lub **/CLR: Safe**, i bezpieczne lub czysty obraz nie może zawierać segmentów danych.  
  
 Zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md) Aby uzyskać więcej informacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2393.  
  
```  
// C2393.cpp  
// compile with: /clr:pure /c  
#pragma data_seg("myseg")  
int n = 0;   // C2393  
```