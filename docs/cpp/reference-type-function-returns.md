---
title: Zwracanie funkcji typu odwołania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function return types [C++], reference type
- data types [C++], function return types
- functions [C++], return types
ms.assetid: 5b73be1d-2dc7-41df-ab0a-adcba36f2ad1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 12b86ee4505792fbc3a90d34ece8e714eb3565ff
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947760"
---
# <a name="reference-type-function-returns"></a>Zwracanie funkcji typu odwołania
Funkcje mogą być zadeklarowane do zwrócenia typu odwołania. Istnieją dwa powody, aby taką deklarację:  
  
-   Informacje zwracane jest wystarczająco duży obiekt, który, zwracanie odwołania jest bardziej wydajne niż zwraca kopię.  
  
-   Typ funkcji musi być wartością l.  
  
-   Do określonego obiektu będzie wykroczy poza zakres, gdy funkcja zwraca.  
  
 Tak samo jak może być bardziej efektywne przekazywanie dużych obiektów *do* funkcji przez odwołanie, również może być bardziej efektywne, aby zwrócić dużych obiektów *z* funkcji przez odwołanie. Odwołanie do zwrócenia protokół eliminuje konieczność obiekt jest kopiowany do lokalizacji tymczasowej przed zwróceniem wyniku.  
  
 Typy zwracane odwołanie również może być przydatne, gdy funkcja musi być wartością l. Najbardziej przeciążonych operatorów należą do tej kategorii, szczególnie operator przypisania. Przeciążone operatory są objęte [przeciążone operatory](../cpp/operator-overloading.md).  
  
## <a name="example"></a>Przykład  
 Należy wziąć pod uwagę `Point` przykładu:  
  
```cpp 
// refType_function_returns.cpp  
// compile with: /EHsc  
  
#include <iostream>  
using namespace std;  
  
class Point  
{  
public:  
// Define "accessor" functions as  
//  reference types.  
unsigned& x();  
unsigned& y();  
private:  
// Note that these are declared at class scope:  
unsigned obj_x;   
unsigned obj_y;   
};  
  
unsigned& Point :: x()  
{  
return obj_x;  
}  
unsigned& Point :: y()  
{  
return obj_y;  
}  
  
int main()  
{  
Point ThePoint;  
// Use x() and y() as l-values.  
ThePoint.x() = 7;  
ThePoint.y() = 9;  
  
// Use x() and y() as r-values.  
cout << "x = " << ThePoint.x() << "\n"  
<< "y = " << ThePoint.y() << "\n";  
}  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```Output  
x = 7  
y = 9  
```  
  
 Należy zauważyć, że funkcje `x` i `y` są deklarowane jako zwracania typów odwołań. Te funkcje można używane po obu stronach instrukcji przypisania.  
  
 Należy zauważyć, że w głównym oknie, obiekt ThePoint pozostaje w zakresie, a w związku z tym jego składowe odwołania są wciąż jest aktywny i można bezpiecznie uzyskać dostęp.  
  
 Deklaracje typu referencyjnego musi zawierać inicjatory, z wyjątkiem w następujących przypadkach:  
  
-   Jawne **extern** deklaracji  
  
-   Deklaracja składowej klasy  
  
-   Deklaracja w obrębie klasy  
  
-   Deklaracja argumentu dla funkcji lub typ zwracany dla funkcji  
  
## <a name="caution-returning-address-of-local"></a>Ostrzeżenie zwracanie adresu lokalnej  
 Jeśli zadeklarujesz obiekt w zakresie lokalnym ten obiekt jest niszczony, gdy funkcja zwraca. Jeśli funkcja zwraca odwołanie do tego obiektu, tego odwołania prawdopodobnie spowoduje naruszenie zasad dostępu w czasie wykonywania, jeśli obiekt wywołujący podejmują próbę użycia odwołania o wartości null.  
  
```cpp 
// C4172 means Don’t do this!!!  
Foo& GetFoo()  
{  
    Foo f;  
    ...  
    return f;  
} // f is destroyed here  
```  
  
 Kompilator generuje ostrzeżenie, w tym przypadku: `warning C4172: returning address of local variable or temporary`. W programach proste jest możliwe, że od czasu do czasu nie naruszenie zasad dostępu wystąpi, jeśli odwołanie jest dostępny przez obiekt wywołujący, zanim zostanie zastąpiony lokalizacji pamięci. Jest to spowodowane szczęścia znaczne zmniejszenie. Uwzględnianie ostrzeżenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołania](../cpp/references-cpp.md)