---
title: noreturn | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: noreturn_cpp
dev_langs: C++
helpviewer_keywords:
- __declspec keyword [C++], noreturn
- noreturn __declspec keyword
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 15df38143ded836b671fdfa17a7c5790a9fe960a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="noreturn"></a>noreturn
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 To `__declspec` atrybut informuje kompilator, że funkcja nie zwraca. W rezultacie, kompilator wie, że kod po wywołaniu **__declspec(noreturn)** funkcji jest nieosiągalny.  
  
 Jeśli kompilator znajdzie funkcji z ścieżka kontrolki, która nie zwraca wartości, generuje ostrzeżenie (C4715) lub komunikat o błędzie (C2202). Jeśli ścieżka kontroli nie można nawiązać połączenia z powodu funkcję, która nigdy nie powraca, możesz użyć **__declspec(noreturn)** Aby uniknąć tego ostrzeżenia lub błędu.  
  
> [!NOTE]
>  Dodawanie **__declspec(noreturn)** funkcji, które powinien zwrócić może spowodować niezdefiniowane zachowanie.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie **else** klauzuli nie zawiera instrukcji return.  Deklarowanie `fatal` jako **__declspec(noreturn)** pozwala uniknąć błąd lub ostrzeżenie.  
  
```  
// noreturn2.cpp  
__declspec(noreturn) extern void fatal () {}  
  
int main() {  
   if(1)  
     return 1;  
   else if(0)  
     return 0;  
   else  
     fatal();  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [__declspec](../cpp/declspec.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)