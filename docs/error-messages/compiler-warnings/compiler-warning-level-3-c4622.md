---
title: "Kompilatora (poziom 3) ostrzeżenie C4622 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4622
dev_langs: C++
helpviewer_keywords: C4622
ms.assetid: d3c879f0-4492-4f4b-b26d-230993f3a933
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 03c6edd3732caad4285848a1acd0176ae8e343ac
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4622"></a>Kompilator C4622 ostrzegawcze (poziom 3)
Zastępowanie informacji o debugowaniu utworzonej podczas tworzenia prekompilowanego nagłówka w pliku obiektu: 'Plik'.  
  
 Informacje CodeView w określonym pliku zostało utracone, jeśli został skompilowany z [/Yu](../../build/reference/yu-use-precompiled-header-file.md) opcji (Używanie prekompilowanych nagłówków).  
  
 Zmień nazwę pliku obiektu (za pomocą [/Fo](../../build/reference/fo-object-file-name.md)) podczas tworzenia lub przy użyciu prekompilowanego nagłówka pliku, a następnie połącz przy użyciu nowego pliku obiektu.