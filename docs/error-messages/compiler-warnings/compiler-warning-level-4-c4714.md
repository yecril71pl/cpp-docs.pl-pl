---
title: "Kompilatora (poziom 4) ostrzeżenie C4714 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4714
dev_langs: C++
helpviewer_keywords: C4714
ms.assetid: 22c7fd0c-899d-4e9b-95f3-725b2c49fb46
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5d49ff1bbf6538965d277b0afdd6c96fd9c71ef0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4714"></a>Kompilator C4714 ostrzegawcze (poziom 4)
Funkcja "function" oznaczona jako __forceinline nie została wbudowana  
  
 Dana funkcja zostały wybrane do rozszerzenie funkcji wbudowanej, ale nie wykonał kompilator ze śródwierszowaniem.  
  
 Mimo że `__forceinline` silniejszych wskazuje do kompilatora niż `__inline`, ze śródwierszowaniem jest nadal wykonywane według uznania kompilatora, ale heurystyki nie są używane do określania korzyści z ze śródwierszowaniem tej funkcji.  
  
 W niektórych przypadkach kompilator będzie niewyrównane konkretną funkcję mechaniczne ze względu na. Na przykład kompilator będzie niewyrównane:  
  
-   Funkcja, jeśli spowodowałoby mieszanie zarówno SEH, jak i C++ EH.  
  
-   Niektóre funkcje z kopią konstruować obiekty przekazany przez wartość po włączeniu - GX/EHs/EHa.  
  
-   Funkcje, zwracając obiekt unwindable przez wartość po włączeniu - GX/EHs/EHa.  
  
-   Funkcji w zestawie wbudowanym w przypadku kompilowania kodu bez - Og/Ox/O1/O2.  
  
-   Funkcje za pomocą listy zmiennych argumentów.  
  
-   Funkcja z **spróbuj** — instrukcja (C++, obsługa wyjątków).  
  
 Poniższy przykład generuje C4714:  
  
```  
// C4714.cpp  
// compile with: /Ob1 /GX /W4  
__forceinline void func1()  
{  
   try  
   {  
   }  
   catch (...)  
   {  
   }  
}  
  
void func2()  
{  
   func1();   // C4714  
}  
  
int main()  
{  
}  
```