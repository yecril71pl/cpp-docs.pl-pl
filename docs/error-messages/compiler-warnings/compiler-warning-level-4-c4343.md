---
title: "Kompilatora (poziom 4) ostrzeżenie C4343 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4343
dev_langs: C++
helpviewer_keywords: C4343
ms.assetid: a721b710-e04f-4d15-b678-e4a2c8fd0181
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e6c45c8a2a595d819ecc6eeb2eb8b69a3b5f864e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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