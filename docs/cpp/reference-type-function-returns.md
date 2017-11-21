---
title: "Zwracanie funkcji typu odwołania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- function return types [C++], reference type
- data types [C++], function return types
- functions [C++], return types
ms.assetid: 5b73be1d-2dc7-41df-ab0a-adcba36f2ad1
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f972664b7e7a72a5b271ecc4e3ad79c32c6cd0e7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="reference-type-function-returns"></a>Zwracanie funkcji typu odwołania
Funkcje mogą być deklarowane jak zwracany typ odwołania. Istnieją dwie przyczyny dokonanie takiego oświadczenia:  
  
-   Informacje są zwracane jest wystarczająco duży obiekt, który, zwracanie odwołania jest bardziej efektywne niż zwracanie kopii.  
  
-   Typ funkcji musi być wartością l-value.  
  
-   Nie przejdzie do określonego obiektu poza zakresem, gdy funkcja zwraca.  
  
 Podobnie jak może być bardziej wydajne, aby przekazać duże obiekty *do* funkcje przez odwołanie, również może być bardziej wydajne, aby zwrócić duże obiekty *z* funkcje przez odwołanie. Protokół odwołanie zwracane eliminuje konieczność obiekt kopiowany do lokalizacji tymczasowej przed zwróceniem.  
  
 Typy zwracane odwołanie również może być przydatne, gdy funkcja musi być wartością l-value. Najbardziej przeciążone operatory należą do tej kategorii, szczególnie operator przypisania. Przeciążone operatory są objęte [przeciążone operatory](../cpp/operator-overloading.md).  
  
## <a name="example"></a>Przykład  
 Należy wziąć pod uwagę `Point` przykład:  
  
```  
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
  
```  
x = 7  
y = 9  
```  
  
 Zwróć uwagę, że funkcje `x` i `y` są deklarowane jako zwracanie typy referencyjne. Po obu stronach instrukcji przypisania można używać tych funkcji.  
  
 Należy też zauważyć, że w głównym, obiekt ThePoint pozostaje w zakresie, a w związku z tym jego elementy członkowskie odwołania są wciąż jest aktywny i mogą bezpiecznie uzyskiwać.  
  
 Deklaracje typów referencyjnych musi zawierać inicjatory z wyjątkiem w następujących przypadkach:  
  
-   Jawne `extern` deklaracji  
  
-   Deklaracja elementu członkowskiego klasy  
  
-   Deklaracja w obrębie klasy  
  
-   Deklaracja argumentu dla funkcji lub typ zwracany dla funkcji  
  
## <a name="caution-returning-address-of-local"></a>Zwracanie adresu lokalnej Uwaga  
 W przypadku obiektu w zakresie lokalnym, ten obiekt zostanie zniszczona po powrocie z funkcji. Jeśli funkcja zwraca odwołanie do tego obiektu, odwołujące się prawdopodobnie spowoduje naruszenie zasad dostępu w czasie wykonywania, jeśli element wywołujący próbuje użyć odwołanie o wartości null.  
  
```  
// C4172 means Don’t do this!!!  
Foo& GetFoo()  
{  
    Foo f;  
    ...  
    return f;  
} // f is destroyed here  
```  
  
 Kompilator generuje ostrzeżenie w tym przypadku: `warning C4172: returning address of local variable or temporary`. W programach proste jest czasami nie naruszenie zasad dostępu będzie wystąpić Jeśli odwołanie jest dostępny przez obiekt wywołujący, zanim zostanie zastąpiony lokalizacji pamięci. Jest to spowodowane szczęścia znaczne zmniejszenie. Uwzględnianie ostrzeżenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołania](../cpp/references-cpp.md)