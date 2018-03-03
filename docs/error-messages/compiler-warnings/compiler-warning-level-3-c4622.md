---
title: "Kompilatora (poziom 3) ostrzeżenie C4622 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4622
dev_langs:
- C++
helpviewer_keywords:
- C4622
ms.assetid: d3c879f0-4492-4f4b-b26d-230993f3a933
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 52f4491d26cfa56f48ed479b30daeafe9cc01adf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4622"></a>Kompilator C4622 ostrzegawcze (poziom 3)
Zastępowanie informacji o debugowaniu utworzonej podczas tworzenia prekompilowanego nagłówka w pliku obiektu: 'Plik'.  
  
 Informacje CodeView w określonym pliku zostało utracone, jeśli został skompilowany z [/Yu](../../build/reference/yu-use-precompiled-header-file.md) opcji (Używanie prekompilowanych nagłówków).  
  
 Zmień nazwę pliku obiektu (za pomocą [/Fo](../../build/reference/fo-object-file-name.md)) podczas tworzenia lub przy użyciu prekompilowanego nagłówka pliku, a następnie połącz przy użyciu nowego pliku obiektu.