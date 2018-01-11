---
title: "out_of_range — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: stdexcept/std::out_of_range
dev_langs: C++
helpviewer_keywords: out_of_range class
ms.assetid: d0e14dc0-065e-4666-9ac9-51e52223c503
caps.latest.revision: "25"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2c92933e62f79b22b988099f0d7cbad1f3679888
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="outofrange-class"></a>out_of_range — Klasa
Klasa służy jako klasa podstawowa dla wszystkich wyjątków zgłaszanych do zgłaszania argument, który jest poza prawidłowym zakresem.  
  
## <a name="syntax"></a>Składnia  
  
```  
class out_of_range : public logic_error {  
public:  
    explicit out_of_range(const string& message);

    explicit out_of_range(const char *message);

};  
```  
  
## <a name="remarks"></a>Uwagi  
 Wartość zwrócona przez [co](../standard-library/exception-class.md) kopię **komunikat**`.`[danych](../standard-library/basic-string-class.md#data).  
  
## <a name="example"></a>Przykład  
  
```cpp  
// out_of_range.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
using namespace std;  
  
int main() {  
// out_of_range  
   try {  
      string str( "Micro" );  
      string rstr( "soft" );  
      str.append( rstr, 5, 3 );  
      cout << str << endl;  
   }  
   catch ( exception &e ) {  
      cerr << "Caught: " << e.what( ) << endl;  
   };  
}  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```  
Caught: invalid string position  
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<stdexcept — >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [logic_error — klasa](../standard-library/logic-error-class.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

