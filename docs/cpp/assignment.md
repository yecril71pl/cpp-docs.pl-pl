---
title: Przypisanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], assignment
- assignment operators [C++], overloaded
ms.assetid: d87e4f89-f8f5-42c1-9d3c-184bca9d0e15
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 66fd08215c3849bf487578b28b1824afbec14c52
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="assignment"></a>Przypisanie
Operator przypisania (**=**) jest mówiąc ściślej, operator binarny. Jego deklaracji jest taki sam jak inne operatora binarnego, z następującymi wyjątkami:  
  
-   Musi być niestatyczną funkcją członkowską. Nie `operator=` mogą być deklarowane jako funkcji nieczłonkowskiej.  
  
-   Nie jest dziedziczone przez klasy pochodnej.  
  
-   Domyślnie `operator=` funkcji mogą być generowane przez kompilator dla typu klasy, jeśli żaden nie istnieje. (Aby uzyskać więcej informacji na temat domyślne `operator=` funkcji, zobacz [Memberwise przypisania i inicjowania](http://msdn.microsoft.com/en-us/94048213-8b49-4416-8069-b1b7a6f271f9).)  
  
 Poniższy przykład przedstawia sposób deklarować operatora przypisania:  
  
```  
// assignment.cpp  
class Point  
{  
public:  
   Point &operator=( Point & );  // Right side is the argument.  
   int _x, _y;  
};  
  
// Define assignment operator.  
Point &Point::operator=( Point &ptRHS )  
{  
   _x = ptRHS._x;  
   _y = ptRHS._y;  
  
   return *this;  // Assignment operator returns left side.  
}  
  
int main()  
{  
}  
```  
  
 Należy pamiętać, że podany argumentu z prawej strony wyrażenia. Operator zwraca obiekt, aby zachować zachowanie operatora przypisania, która zwraca wartość po lewej stronie, po zakończeniu przydziału. Umożliwia to pisanie instrukcji, takich jak:  
  
```  
pt1 = pt2 = pt3;  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przeładowanie operatora](../cpp/operator-overloading.md)