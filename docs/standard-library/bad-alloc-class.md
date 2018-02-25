---
title: "bad_alloc — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- new/std::bad_alloc
dev_langs:
- C++
helpviewer_keywords:
- bad_alloc class
ms.assetid: 6429a8e6-5a49-4907-8d56-f4a4ec8131d0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d338b155eaebd7678e611dd38b8e1ef230545eb5
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="badalloc-class"></a>bad_alloc — Klasa
Klasa opisuje wyjątek, aby wskazać, że żądanie alokacji nie powiodła się.  
  
## <a name="syntax"></a>Składnia  
  
```  
class bad_alloc : public exception {  
    bad_alloc();
virtual ~bad_alloc();

};  
```  
  
## <a name="remarks"></a>Uwagi  
 Wartość zwrócona przez **co** to ciąg C zdefiniowane w implementacji. Brak funkcji Członkowskich generują żadnych wyjątków.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<nowy >  
  
 **Namespace:** Standard  
  
## <a name="example"></a>Przykład  
  
```cpp  
// bad_alloc.cpp  
// compile with: /EHsc  
#include<new>  
#include<iostream>  
using namespace std;  
  
int main() {  
   char* ptr;  
   try {  
      ptr = new char[(~unsigned int((int)0)/2) - 1];  
      delete[] ptr;  
   }  
   catch( bad_alloc &ba) {  
      cout << ba.what( ) << endl;  
   }  
}  
```  
  
## <a name="sample-output"></a>Przykładowe dane wyjściowe  
  
```  
bad allocation  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<nowy >  
  
## <a name="see-also"></a>Zobacz też
 [exception, klasa](../standard-library/exception-class.md)  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

