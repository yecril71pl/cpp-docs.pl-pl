---
title: Kompilatora (poziom 1) ostrzeżenie C4946 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4946
dev_langs:
- C++
helpviewer_keywords:
- C4946
ms.assetid: b85cbef0-e053-4de6-9b14-7b0f82d40495
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 072e43f4750d2f64fb0f9dc56478a68699b98c9e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33291934"
---
# <a name="compiler-warning-level-1-c4946"></a>Kompilator C4946 ostrzegawcze (poziom 1)
reinterpret_cast używane między pokrewnymi klasami: 'klasa1' i 'klasa2'  
  
 Nie używaj [reinterpret_cast](../../cpp/reinterpret-cast-operator.md) można rzutować między powiązanych typów. Użyj [static_cast](../../cpp/static-cast-operator.md) w zamian lub na typach polimorficznych użyj [dynamic_cast](../../cpp/dynamic-cast-operator.md).  
  
 Domyślnie to ostrzeżenie jest wyłączone. Aby uzyskać więcej informacji, zobacz [kompilatora ostrzeżeń czy są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
 Poniższy przykład kodu generuje C4946:  
  
```  
// C4946.cpp  
// compile with: /W1  
#pragma warning (default : 4946)  
class a {  
public:  
   a() : m(0) {}  
   int m;  
};  
  
class b : public virtual a {  
};  
  
class b2 : public virtual a {  
};  
  
class c : public b, public b2 {  
};  
  
int main() {  
   c* pC = new c;  
   a* pA = reinterpret_cast<a*>(pC);   // C4946  
   // try the following line instead  
   // a* pA = static_cast<a*>(pC);  
}  
```