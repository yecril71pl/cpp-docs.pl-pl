---
title: "Kompilatora (poziom 4) ostrzeżenie C4324 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4324
dev_langs: C++
helpviewer_keywords: C4324
ms.assetid: 420fa929-d9c0-40b4-8808-2d8ad3ca8090
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6ef3e94e84621de6cd19bf7abba9c3d21b8d3eef
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4324"></a>Kompilator C4324 ostrzegawcze (poziom 4)
"struct_name": struktura została wzmocniona ze względu na __declspec(align())  
  
 Dopełnienie został dodany na końcu struktury, ponieważ określona [__declspec(align)](../../cpp/align-cpp.md) wartości.  
  
 Na przykład następujący kod generuje C4324:  
  
```  
// C4324.cpp  
// compile with: /W4  
struct __declspec(align(32)) A  
{  
   char a;  
};   // C4324  
  
int main()  
{  
}  
```