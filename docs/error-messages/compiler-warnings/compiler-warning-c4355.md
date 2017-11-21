---
title: "C4355 ostrzeżenia kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4355
dev_langs: C++
helpviewer_keywords: C4355
ms.assetid: b819ecab-8a07-42d7-8fa4-1180d51626c0
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 061ad3df17cf9c86fbc5ac98048932aff8b0b25b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-c4355"></a>C4355 ostrzeżenia kompilatora
'this': używany na liście inicjatora bazowego elementu członkowskiego  
  
 **To** wskaźnika jest prawidłowy tylko wewnątrz Niestatyczne funkcje Członkowskie. Nie można użyć na liście inicjatora dla klasy podstawowej.  
  
 Klasa podstawowa konstruktorów i konstruktorów elementu członkowskiego klasy są wywoływane przed **to** konstruktora. W efekcie zrealizowaniu wskaźnik do obiektu unconstructed do innego konstruktora. Jeśli te inne konstruktorów dostęp do wszelkich elementów członkowskich lub wywoływać funkcje Członkowskie na tym, wynik będzie niezdefiniowany. Nie należy używać **to** wskaźnika dopiero po ukończeniu wszystkich konstrukcji.  
  
 To ostrzeżenie jest domyślnie wyłączone. Zobacz [kompilatora ostrzeżeń czy są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.  
  
 Poniższy przykład generuje C4355:  
  
```  
// C4355.cpp  
// compile with: /w14355 /c  
#include <tchar.h>  
  
class CDerived;  
class CBase {  
public:  
   CBase(CDerived *derived): m_pDerived(derived) {};  
   ~CBase();  
   virtual void function() = 0;  
  
   CDerived * m_pDerived;  
};  
  
class CDerived : public CBase {  
public:  
   CDerived() : CBase(this) {};   // C4355 "this" used in derived c'tor  
   virtual void function() {};  
};  
  
CBase::~CBase() {  
   m_pDerived -> function();  
}  
  
int main() {  
   CDerived myDerived;  
}  
```