---
title: "bad_cast — wyjątek | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- bad_cast
- bad_cast_cpp
dev_langs:
- C++
helpviewer_keywords:
- exceptions [C++], bad_cast
- bad_cast keyword [C++]
ms.assetid: 31eae1e7-d8d5-40a0-9fef-64a6a4fc9021
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d7880a01f247d5dc3cce5a6f247297ef65289367
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="badcast-exception"></a>bad_cast — Wyjątek
`bad_cast` Wyjątku przez `dynamic_cast` operatora w wyniku nie powiodło się Rzutowanie na typ referencyjny.  
  
## <a name="syntax"></a>Składnia  
  
```  
catch (bad_cast)  
   statement  
```  
  
## <a name="remarks"></a>Uwagi  
 Interfejs dla `bad_cast` jest:  
  
```  
class bad_cast : public exception {  
public:  
   bad_cast(const char * _Message = "bad cast");  
   bad_cast(const bad_cast &);  
   virtual ~bad_cast();  
};  
```  
  
 Poniższy kod zawiera przykład nieudanej `dynamic_cast` który zgłasza `bad_cast` wyjątku.  
  
```  
// expre_bad_cast_Exception.cpp  
// compile with: /EHsc /GR  
#include <typeinfo.h>  
#include <iostream>  
  
class Shape {  
public:  
   virtual void virtualfunc() const {}  
};  
  
class Circle: public Shape {  
public:  
   virtual void virtualfunc() const {}  
};  
  
using namespace std;  
int main() {  
   Shape shape_instance;  
   Shape& ref_shape = shape_instance;  
   try {  
      Circle& ref_circle = dynamic_cast<Circle&>(ref_shape);   
   }  
   catch (bad_cast b) {  
      cout << "Caught: " << b.what();  
   }  
}  
```  
  
 Wyjątek jest generowany, gdy jest rzutowanie obiektu (kształtu) nie pochodzi od typu określone rzutowanie (okrąg). Aby uniknąć tego wyjątku, Dodaj następujące deklaracje `main`:  
  
```  
Circle circle_instance;  
Circle& ref_circle = circle_instance;  
```  
  
 Wycofać rzutowania w tym sensie `try` zablokować w następujący sposób:  
  
```  
Shape& ref_shape = dynamic_cast<Shape&>(ref_circle);  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Operator dynamic_cast](../cpp/dynamic-cast-operator.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)   
 [Obsługa wyjątków języka C++](../cpp/cpp-exception-handling.md)