---
title: __super | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __super_cpp
dev_langs:
- C++
helpviewer_keywords:
- __super keyword [C++]
ms.assetid: f0957c31-9256-405b-b402-cad182404b5f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 93585337ae34e7c95d1c11b0a970afc8b36987bb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="super"></a>__super
**Dotyczące firmy Microsoft**  
  
 Można jawnie określać dla funkcji, które są zastępowanie wywoływania implementacji klasy podstawowej.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
__super::  
member_function  
();  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Podczas fazy rozpoznawanie przeciążenia uwzględniane są wszystkie dostępne metody klasy podstawowej, a funkcja, która udostępnia najlepsze dopasowanie jest tą, która jest wywoływana.  
  
 `__super`może wystąpić tylko w treści funkcji członkowskiej.  
  
 `__super`Nie można używać z używającego deklaracji. Zobacz [za pomocą deklaracji](../cpp/using-declaration.md) Aby uzyskać więcej informacji.  
  
 Wraz z wprowadzeniem [atrybuty](../windows/cpp-attributes-reference.md) który wstrzyknięcie kodu, kod może zawierać co najmniej jednej klasy podstawowej nazwy, których użytkownik może nie wiedzieć, lecz zawiera metody, które chcesz wywołać.  
  
## <a name="example"></a>Przykład  
  
```  
// deriv_super.cpp  
// compile with: /c  
struct B1 {  
   void mf(int) {}  
};  
  
struct B2 {  
   void mf(short) {}  
  
   void mf(char) {}  
};  
  
struct D : B1, B2 {  
   void mf(short) {  
      __super::mf(1);   // Calls B1::mf(int)  
      __super::mf('s');   // Calls B2::mf(char)  
   }  
};  
```  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Słowa kluczowe](../cpp/keywords-cpp.md)