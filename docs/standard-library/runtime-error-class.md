---
title: "runtime_error — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: stdexcept/std::runtime_error
dev_langs: C++
helpviewer_keywords: runtime_error class
ms.assetid: 4d0227bf-847b-45a2-a320-2351ebf98368
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 25153052fff20635069340e3d0c9f46f3d56280c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="runtimeerror-class"></a>runtime_error — Klasa
Klasa służy jako klasa podstawowa dla wszystkich wyjątków zgłaszanych może raportować błędy prawdopodobnie wykrywalny, tylko wtedy, gdy program jest wykonywana.  
  
## <a name="syntax"></a>Składnia  
  
```  
class runtime_error : public exception {  
public:  
    explicit runtime_error(const string& message);

    explicit runtime_error(const char *message);

};  
```  
  
## <a name="remarks"></a>Uwagi  
 Wartość zwrócona przez [wyjątek klasy](../standard-library/exception-class.md) kopię **komunikat**`.`[danych](../standard-library/basic-string-class.md#data).  
  
## <a name="example"></a>Przykład  
  
```cpp  
// runtime_error.cpp  
// compile with: /EHsc /GR  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
// runtime_error  
   try   
   {  
      locale loc( "test" );  
   }  
   catch ( exception &e )   
   {  
      cerr << "Caught " << e.what( ) << endl;  
      cerr << "Type " << typeid( e ).name( ) << endl;  
   };  
}  
\* Output:   
Caught bad locale name  
Type class std::runtime_error  
*\  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<stdexcept — >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
[Klasa Exception](../standard-library/exception-class.md)

    
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

