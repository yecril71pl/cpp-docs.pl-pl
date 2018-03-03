---
title: "C2299 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2299
dev_langs:
- C++
helpviewer_keywords:
- C2299
ms.assetid: d001c2bc-f6fd-47aa-8e42-0eb824d6441d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8190511605a7f01dc399e1d8a8b4af96477fa407
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2299"></a>C2299 błąd kompilatora
"Funkcja": Zmiana zachowania: jawna specjalizacja nie może być Konstruktor kopiujący lub kopia operatora przypisania  
  
 Ten błąd może być również generowany w wyniku pracy zgodność kompilatora, która została wykonana dla Visual C++ 2005: poprzedniej wersji programu Visual C++ dozwolony jawne specjalizacje Konstruktor kopiujący lub kopia operatora przypisania.  
  
 Aby rozwiązać C2299, nie należy wprowadzać Konstruktor kopiujący lub operator przypisania funkcji szablonu, ale raczej funkcji nieszablonowe, która przyjmuje typu klasy. Wszelki kod, który wywołuje Konstruktor kopiujący lub operator przypisania przez jawne określenie argumentów szablonu musi usunąć argumenty szablonu.  
  
 Poniższy przykład generuje C2299:  
  
```  
// C2299.cpp  
// compile with: /c  
class C {  
   template <class T>  
   C (T t);  
  
   template <> C (const C&);   // C2299  
   C (const C&);   // OK  
};  
```