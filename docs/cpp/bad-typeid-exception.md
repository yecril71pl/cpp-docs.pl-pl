---
title: "bad_typeid — wyjątek | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- bad_typeid
- bad_typeid_cpp
dev_langs:
- C++
helpviewer_keywords:
- bad_typeid exception
- exceptions [C++], bad_typeid
ms.assetid: 5963ed58-4ede-4597-957d-f7bbd06299c2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9409bd83132877f73b58e12cb9503c41a3dc3cf9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="badtypeid-exception"></a>bad_typeid — Wyjątek
`bad_typeid` Wyjątku przez [operatora typeid](../cpp/typeid-operator.md) podczas argument `typeid` wskaźnik NULL.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      catch (bad_typeid)  
   statement  
```  
  
## <a name="remarks"></a>Uwagi  
 Interfejs dla `bad_typeid` jest:  
  
```  
class bad_typeid : public exception  
{  
public:  
   bad_typeid(const char * _Message = "bad typeid");  
   bad_typeid(const bad_typeid &);  
   virtual ~bad_typeid();  
};  
```  
  
 W poniższym przykładzie przedstawiono `typeid` operator zgłaszanie `bad_typeid` wyjątku.  
  
```  
// expre_bad_typeid.cpp  
// compile with: /EHsc /GR  
#include <typeinfo.h>  
#include <iostream>  
  
class A{  
public:  
   // object for class needs vtable  
   // for RTTI  
   virtual ~A();  
};  
  
using namespace std;  
int main() {  
A* a = NULL;  
  
try {  
   cout << typeid(*a).name() << endl;  // Error condition  
   }  
catch (bad_typeid){  
   cout << "Object is NULL" << endl;  
   }  
}  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```  
Object is NULL  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Informacje typu Run-Time](../cpp/run-time-type-information.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)