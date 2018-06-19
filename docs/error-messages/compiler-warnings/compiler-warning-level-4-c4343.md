---
title: Kompilatora (poziom 4) ostrzeżenie C4343 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4343
dev_langs:
- C++
helpviewer_keywords:
- C4343
ms.assetid: a721b710-e04f-4d15-b678-e4a2c8fd0181
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 300bab652c88322ef7e3b28cbf2cafe304d361d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302337"
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