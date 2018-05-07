---
title: Kompilatora (poziom 4) ostrzeżenie C4263 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4263
dev_langs:
- C++
helpviewer_keywords:
- C4263
ms.assetid: daabb05d-ab56-460f-ab6c-c74d222ef649
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 883b36e524f3631811cf503ebc695e3c4ad53da2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4263"></a>Kompilator C4263 ostrzegawcze (poziom 4)
"Funkcja": funkcja członkowska nie przesłania wszelkie klasa podstawowa wirtualnej funkcji członkowskiej  
  
 Definicja funkcji klasy ma taką samą nazwę jak funkcji wirtualnej klasy podstawowej, ale nie sam numer lub typy argumentów. Spowoduje to skutecznie ukrycie funkcję wirtualną w klasie podstawowej.  
  
 To ostrzeżenie jest domyślnie wyłączone. Zobacz [kompilatora ostrzeżeń czy są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.  
  
 Poniższy przykład generuje C4263:  
  
```  
// C4263.cpp  
// compile with: /W4  
#pragma warning(default:4263)  
#pragma warning(default:4264)  
class B {  
public:  
   virtual void func();  
};  
  
class D : public B {  
   void func(int);   // C4263  
};  
  
int main() {  
}  
```