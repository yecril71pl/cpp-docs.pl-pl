---
title: Kompilatora (poziom 3) ostrzeżenie C4622 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4622
dev_langs:
- C++
helpviewer_keywords:
- C4622
ms.assetid: d3c879f0-4492-4f4b-b26d-230993f3a933
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0b82e87f37b50b8df727d043889cb35ca02d3f78
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4622"></a>Kompilator C4622 ostrzegawcze (poziom 3)
Zastępowanie informacji o debugowaniu utworzonej podczas tworzenia prekompilowanego nagłówka w pliku obiektu: 'Plik'.  
  
 Informacje CodeView w określonym pliku zostało utracone, jeśli został skompilowany z [/Yu](../../build/reference/yu-use-precompiled-header-file.md) opcji (Używanie prekompilowanych nagłówków).  
  
 Zmień nazwę pliku obiektu (za pomocą [/Fo](../../build/reference/fo-object-file-name.md)) podczas tworzenia lub przy użyciu prekompilowanego nagłówka pliku, a następnie połącz przy użyciu nowego pliku obiektu.