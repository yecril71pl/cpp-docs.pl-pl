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
ms.openlocfilehash: c6343d7be23e633fe383343bd7f154d5cc9bb234
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39407614"
---
# <a name="assignment"></a>Przypisanie
Operator przypisania (**=**) jest ściśle rzecz ujmując, operatora binarnego. Jego deklaracji jest taka sama jak innych operatora binarnego, z następującymi wyjątkami:  
  
-   Musi być funkcją składową Niestatyczne. Nie **operator =** mogą być deklarowane jako funkcja niebędących.  
  
-   Nie jest dziedziczone przez klasy pochodne.  
  
-   Domyślnie **operator =** funkcji mogą być generowane przez kompilator dla typu klasy, jeśli żaden nie istnieje.  
  
 Poniższy przykład ilustruje sposób deklarowania operatora przypisania:  
  
```cpp 
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
  
 Należy pamiętać, że podany argument po prawej stronie wyrażenia. Operator zwraca obiekt, aby zachować zachowanie operator przypisania zwraca wartość po lewej stronie, po zakończeniu przydziału. Dzięki temu można pisać instrukcje, takich jak:  
  
```cpp 
pt1 = pt2 = pt3;  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Przeładowanie operatora](../cpp/operator-overloading.md)