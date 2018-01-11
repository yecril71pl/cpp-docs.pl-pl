---
title: "Kompilatora (poziom 1) ostrzeżenie C4086 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4086
dev_langs: C++
helpviewer_keywords: C4086
ms.assetid: 9248831b-22bf-47af-8684-bfadb17e94fc
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 120c8cf15cc4d4c320c422feffed908276c52d3d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4086"></a>Kompilator C4086 ostrzegawcze (poziom 1)
Oczekiwano wartości parametru pragma "1", "2", "4", "8", lub "16"  
  
 Wartości parametru pragma nie ma wymaganej wartości (1, 2, 4, 8 lub 16).  
  
## <a name="example"></a>Przykład  
  
```  
// C4086.cpp  
// compile with: /W1 /LD  
#pragma pack( 3 ) // C4086  
```