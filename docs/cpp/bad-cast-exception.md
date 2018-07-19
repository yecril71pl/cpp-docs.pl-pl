---
title: bad_cast — wyjątek | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b50995ff1d5eb730bf6593679194d32d5300b9d7
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947740"
---
# <a name="badcast-exception"></a>bad_cast — Wyjątek
`bad_cast` Wyjątek jest generowany przez `dynamic_cast` operatora w wyniku zakończone niepowodzeniem Rzutowanie na typ odwołania.  
  
## <a name="syntax"></a>Składnia  
  
```  
catch (bad_cast)  
   statement  
```  
  
## <a name="remarks"></a>Uwagi  
 Interfejs `bad_cast` jest:  
  
```cpp 
class bad_cast : public exception {  
public:  
   bad_cast(const char * _Message = "bad cast");  
   bad_cast(const bad_cast &);  
   virtual ~bad_cast();  
};  
```  
  
 Poniższy kod zawiera przykład niepowodzenia `dynamic_cast` która zgłasza `bad_cast` wyjątku.  
  
```cpp 
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
  
 Wyjątek jest zgłaszany, ponieważ obiekt rzutowany (kształt) nie pochodzi od typu określone rzutowanie (Circle). Aby uniknąć wyjątek, należy dodać te deklaracje **głównego**:  
  
```cpp 
Circle circle_instance;  
Circle& ref_circle = circle_instance;  
```  
  
 Wycofać poczucie rzutowanie w **spróbuj** blokowania w następujący sposób:  
  
```cpp 
Shape& ref_shape = dynamic_cast<Shape&>(ref_circle);  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Operator dynamic_cast](../cpp/dynamic-cast-operator.md)   
 [Keywords](../cpp/keywords-cpp.md)   
 [Obsługa wyjątków języka C++](../cpp/cpp-exception-handling.md)