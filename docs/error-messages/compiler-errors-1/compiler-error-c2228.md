---
title: C2228 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2228
dev_langs:
- C++
helpviewer_keywords:
- C2228
ms.assetid: 901cadb1-ce90-4ae0-a360-547a9ba2ca18
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 969f622877c60bdc340dedf8a2416ac56b2ad0e0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171028"
---
# <a name="compiler-error-c2228"></a>C2228 błąd kompilatora
po lewej ".identifier" musi mieć klasy/struktury/Unii  
  
 Argument po lewej kropki (.) nie jest klasy, struktury lub związku.  
  
 Poniższy przykład generuje C2228:  
  
```  
// C2228.cpp  
int i;  
struct S {  
public:  
    int member;  
} s, *ps = &s;  
  
int main() {  
   i.member = 0;   // C2228 i is not a class type  
   ps.member = 0;  // C2228 ps is a pointer to a structure  
  
   s.member = 0;   // s is a structure type  
   ps->member = 0; // ps points to a structure S  
}  
```  
  
 Ten błąd będzie również sprawdzić, korzystając z niepoprawną składnię podczas korzystania z rozszerzeń zarządzanych. W innych językach Visual Studio umożliwia kropka uzyskiwanie dostępu do członka klasy zarządzanej, wskaźnik do obiektu w języku C++ oznacza, należy użyć -> — operator można uzyskać dostępu do elementu członkowskiego:  
  
 Problem: `String * myString = checkedListBox1->CheckedItems->Item[0].ToString();`  
  
 Prawa: `String * myString = checkedListBox1->CheckedItems->Item[0]->ToString();`