---
title: "Ciąg oraz -O formatowania (Modern C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 3954e8de-a59b-4175-89c9-4ee842ab89ed
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a13861fe03547e37c4de72c21a528e297a217511
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="string-and-io-formatting-modern-c"></a>Formatowanie ciągów i we/wy (Modern C++)
C++ [iostream](../standard-library/iostream.md) są w stanie ciąg sformatowany we/wy. Na przykład poniższy kod przedstawia sposób ustawiania cout będą formatowane liczby całkowitej w celu danych wyjściowych w formacie szesnastkowym, najpierw zapisywanie poza bieżący stan i ponownie ustawienia później, gdy stan formatowania jest przekazywana do cout, pozostaje on objęty w ten sposób do momentu zmiany, nie tylko dla jednego wiersza kodu.  
  
```cpp  
#include <iostream>  
#include <iomanip>  
  
using namespace std;  
  
int main()   
{  
    ios state(nullptr);  
  
    cout << "The answer in decimal is: " << 42 << endl;  
  
    state.copyfmt(cout); // save current formatting  
    cout << "In hex: 0x" // now load up a bunch of formatting modifiers  
        << hex   
        << uppercase   
        << setw(8)   
        << setfill('0')   
        << 42            // the actual value we wanted to print out  
        << endl;  
    cout.copyfmt(state); // restore previous formatting  
}  
  
```  
  
 Może to być całkowicie zbyt skomplikowane, w wielu przypadkach. Alternatywnie można użyć Boost.Format z biblioteki języka C++ zwiększenie wydajności, nawet jeśli komputer jest niestandardowy. Możesz pobrać żadnej biblioteki zwiększanie wyniku z [zwiększanie wyniku](http://www.boost.org/) witryny sieci Web.  
  
 Niektóre zalety Boost.Format są następujące:  
  
-   Palety: Bezpieczne i zgłasza wyjątek błędy — na przykład specyfikację zbyt małej lub zbyt wiele elementów.  
  
-   Rozszerzalne: Działa w przypadku dowolnego typu, który można przesłać strumieniowo.  
  
-   Wygodna: Standard Posix i podobne ciągi formatów.  
  
 Chociaż Boost.Format jest oparty na języku C++ [iostream](../standard-library/iostream-programming.md), które są bezpieczne i rozszerzony, nie są zoptymalizowane pod kątem wydajności. Jeśli wymagasz, aby zoptymalizować wydajność, należy wziąć pod uwagę C [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) i [sprintf —](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md), które są szybkie i łatwe w użyciu. Jednak nie są one rozszerzalnych lub bezpieczne przed lukami w zabezpieczeniach. (Istnieją bezpieczne wersje, ale ich pociągnąć za sobą zmniejszenie wydajności niewielkie. Aby uzyskać więcej informacji, zobacz [printf_s —, _printf_s_l —, wprintf_s —, _wprintf_s_l —](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md) i [sprintf_s —, _sprintf_s_l —, swprintf_s —, _swprintf_s_l —](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)).  
  
 Poniższy kod przedstawia niektóre funkcje formatowania zwiększanie wyniku.  
  
```cpp  
    string s = str( format("%2% %2% %1%\n") % "world" % "hello" );  
    // s contains "hello hello world"    
  
    for( auto i = 0; i < names.size(); ++i )  
        cout << format("%1% %2% %|40t|%3%\n") % first[i] % last[i] % tel[i];  
    // Georges Benjamin Clemenceau             +33 (0) 123 456 789  
    // Jean de Lattre de Tassigny              +33 (0) 987 654 321  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zapraszamy ponownie do języka C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)   
 [Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)   
 [\<iostream — >](../standard-library/iostream.md)   
 [\<limity >](../standard-library/limits.md)   
 [\<iomanip — >](../standard-library/iomanip.md)
