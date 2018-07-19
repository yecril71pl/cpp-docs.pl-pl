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
ms.openlocfilehash: 27e78f7429c4d2a0f83ff7184460eb2ae69df129
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38960989"
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
  
## <a name="see-also"></a>Zobacz też  
 [Przeładowanie operatora](../cpp/operator-overloading.md)