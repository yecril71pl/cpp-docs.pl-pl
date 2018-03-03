---
title: "Kompilatora (poziom 4) ostrzeżenie C4343 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4343
dev_langs:
- C++
helpviewer_keywords:
- C4343
ms.assetid: a721b710-e04f-4d15-b678-e4a2c8fd0181
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bf7ab18e58a7c77da42e6497c39e716b632d2f7b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4343"></a>Kompilator C4343 ostrzegawcze (poziom 4)
\#pragma optimize("g",off) przesłania opcję /Og  
  
 To ostrzeżenie, tylko prawidłowe w kompilatorze rodziny procesora Itanium (IPF) zgłasza, że pragma [zoptymalizować](../../preprocessor/optimize.md) overrode [/Og](../../build/reference/og-global-optimizations.md) — opcja kompilatora.  
  
 Poniższy przykład generuje C4343:  
  
```  
// C4343.cpp  
// compile with: /Og /W4 /LD  
// processor: IPF  
#pragma optimize ("g", off)   // C4343  
```