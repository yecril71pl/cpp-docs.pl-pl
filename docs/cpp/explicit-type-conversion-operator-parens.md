---
title: 'Operator jawnej konwersji typu: () | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- explicit data type conversion operator
- conversions [C++], explicit
- operators [C++], explicit type conversion
- data type conversion [C++], explicit
- type conversion [C++], explicit conversions
ms.assetid: 54272006-5ffb-45ed-8283-27152ab97529
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 806a943ff9f5ebd0c6971340b66266aa7da9c0c3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="explicit-type-conversion-operator-"></a>Operator jawnej konwersji typu: ()
Język C++ pozwala na jawną konwersję typu przy użyciu składni podobnej do składni wywołania funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
simple-type-name ( expression-list )  
```  
  
## <a name="remarks"></a>Uwagi  
 A *nazwy typu prostego* następuje *lista wyrażeń* ujęta w nawiasy konstrukcji obiektu określonego typu przy użyciu określonego wyrażenia. W poniższym przykładzie pokazano jawną konwersję typu na typ int.  
  
```  
int i = int( d );  
```  
  
 W poniższym przykładzie przedstawiono `Point` klasy.  
  
## <a name="example"></a>Przykład  
  
```  
// expre_Explicit_Type_Conversion_Operator.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
class Point  
{  
public:  
    // Define default constructor.  
    Point() { _x = _y = 0; }  
    // Define another constructor.  
    Point( int X, int Y ) { _x = X; _y = Y; }  
  
    // Define "accessor" functions as  
    // reference types.  
    unsigned& x() { return _x; }  
    unsigned& y() { return _y; }  
    void Show()   { cout << "x = " << _x << ", "  
                         << "y = " << _y << "\n"; }  
private:  
    unsigned _x;  
    unsigned _y;  
};  
  
int main()  
{  
    Point Point1, Point2;  
  
    // Assign Point1 the explicit conversion  
    //  of ( 10, 10 ).  
    Point1 = Point( 10, 10 );  
  
    // Use x() as an l-value by assigning an explicit  
    //  conversion of 20 to type unsigned.  
    Point1.x() = unsigned( 20 );  
    Point1.Show();  
  
    // Assign Point2 the default Point object.  
    Point2 = Point();  
    Point2.Show();  
}  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```  
x = 20, y = 10  
x = 0, y = 0  
```  
  
 Mimo że w poprzednim przykładzie zademonstrowano jawną konwersję typu przy użyciu stałych, ta sama technika działa przy wykonywaniu konwersji na obiektach. Potwierdza to następujący fragment kodu:  
  
```  
int i = 7;  
float d;  
  
d = float( i );  
```  
  
 Jawne konwersje typu mogą być również określone przy użyciu składni „rzutowania”. Poprzedni przykład przepisany przy użyciu składni rzutowania:  
  
```  
d = (float)i;  
```  
  
 Zarówno rzutowanie, jak i konwersje w stylu funkcji, dają te same wyniki podczas konwertowania z pojedynczych wartości. Jednakże, w składni stylu funkcji można określić więcej niż jeden argument do konwersji. Różnica jest ważna dla typów zdefiniowanych przez użytkownika. Rozważ klasę `Point` i jej konwersje:  
  
```  
struct Point  
{  
    Point( short x, short y ) { _x = x; _y = y; }  
    ...  
    short _x, _y;  
};  
...  
Point pt = Point( 3, 10 );  
```  
  
 Poprzedniego przykładu, który używa stylu funkcji konwersji, pokazano, jak przekonwertować dwóch wartości (po jednej dla *x* i jeden dla *y*) na typ zdefiniowany przez użytkownika `Point`.  
  
> [!CAUTION]
>  Użyj jawnej konwersji typu z rozwagą, gdyż zastępuje ona kontrolę typów wbudowaną w kompilator C++.  
  
 [Rzutowania](../cpp/cast-operator-parens.md) notacji muszą być używane do konwersji na typy, które nie mają *nazwy typu prostego* (wskaźnik lub odwołanie typów, na przykład). Konwersji do typów, które można wyrazić przy *nazwy typu prostego* mogą być napisane w obu formularzy. Zobacz [specyfikatorze typu](http://msdn.microsoft.com/en-us/34b6c737-0ef1-4470-9b77-b26e46c0bbd4) informacje, co stanowi *nazwy typu prostego*.  
  
 W ramach rzutowań niedozwolone są definicje typu.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia przyrostków](../cpp/postfix-expressions.md)   
 [Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)