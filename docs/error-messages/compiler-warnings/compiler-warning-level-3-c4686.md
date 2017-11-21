---
title: "Kompilatora (poziom 3) ostrzeżenie C4686 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4686
dev_langs: C++
helpviewer_keywords: C4686
ms.assetid: 767c83c2-9e4b-4f9e-88c8-02128ba563f4
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 576e714937f0066a7b60ebf38d821715d4157b11
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="compiler-warning-level-3-c4686"></a>Kompilator C4686 ostrzegawcze (poziom 3)
**'**   
 ***Typ zdefiniowany przez użytkownika* ": możliwe zmiany w zachowaniu, zmiana UDT zwracać konwencji wywoływania**  
  
 Specjalizacja szablonu klasy nie jest zdefiniowany, zanim została użyta w zwracanego typu. Wszystko, co tworzy wystąpienie klasy rozwiąże C4686; deklarowanie wystąpienia lub dostęp do elementu członkowskiego (C\<int >:: niczego) są także opcje.  
  
 To ostrzeżenie jest domyślnie wyłączone. Zobacz [kompilatora ostrzeżeń czy są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.  
  
 Zamiast tego należy spróbować wykonać następujące czynności  
  
```  
// C4686.cpp  
// compile with: /W3  
#pragma warning (default : 4686)  
template <class T>  
class C;  
  
template <class T>  
C<T> f(T);  
  
template <class T>  
class C {};  
  
int main() {  
   f(1);   // C4686  
}  
  
template <class T>  
C<T> f(T) {  
   return C<int>();  
}  
```