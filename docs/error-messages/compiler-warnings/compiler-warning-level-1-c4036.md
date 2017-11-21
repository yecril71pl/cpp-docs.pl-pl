---
title: "Kompilatora (poziom 1) ostrzeżenie C4036 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4036
dev_langs: C++
helpviewer_keywords: C4036
ms.assetid: f0b15359-4d62-48ec-8cb1-a7b36587a47f
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6392ba12c14ca3ef89f992e358bf019d1d92e5db
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4036"></a>Kompilator C4036 ostrzegawcze (poziom 1)
bez nazwy "type" jako rzeczywisty parametr  
  
 Nazwa typu, nie jest określony dla struktury, Unii, wyliczenie lub klasy używane jako rzeczywisty parametr. Jeśli używasz [/Zg](../../build/reference/zg-generate-function-prototypes.md) do Generuj prototypy funkcji, kompilator generuje to ostrzeżenie i komentarze parametrów formalnych w wygenerowanym prototypu.  
  
 Określ nazwę typu, aby rozwiązać to ostrzeżenie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4036.  
  
```  
// C4036.c  
// compile with: /Zg /W1  
// D9035 expected  
typedef struct { int i; } T;  
void f(T* t) {}   // C4036  
  
// OK  
typedef struct MyStruct { int i; } T2;  
void f2(T2 * t) {}  
```