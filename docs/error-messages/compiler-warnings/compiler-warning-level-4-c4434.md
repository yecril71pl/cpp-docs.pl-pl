---
title: "Kompilatora (poziom 4) ostrzeżenie C4434 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4434
dev_langs: C++
helpviewer_keywords: C4434
ms.assetid: 24b8785e-353a-4c37-8bed-ed61001a871d
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a9499d145263c3bbb1bd5aac948c6be9e4db48d2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4434"></a>Kompilator C4434 ostrzegawcze (poziom 4)
Konstruktor klasy musi posiadać prywatną dostępność; Zmiana na prywatny dostęp  
  
 C4434 oznacza, że kompilator zmieniony dostępność Konstruktor statyczny. Konstruktory statyczne musi posiadać prywatną dostępność, ponieważ są one przeznaczone tylko do wywołania przez środowisko uruchomieniowe języka wspólnego. Aby uzyskać więcej informacji, zobacz [konstruktory statyczne](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Static_constructors).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4434.  
  
```  
// C4434.cpp  
// compile with: /W4 /c /clr  
public ref struct R {  
   static R(){}   // C4434  
};  
```