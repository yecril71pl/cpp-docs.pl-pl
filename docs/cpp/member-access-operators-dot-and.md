---
title: "Operatory dostępu do elementów członkowskich:. i -&gt; | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- .
- ->
dev_langs: C++
helpviewer_keywords:
- member access, expressions
- operators [C++], member access
- dot operator (.)
- -> operator
- member access, operators
- postfix operators [C++]
- . operator
- member access
ms.assetid: f8fc3df9-d728-40c5-b384-276927f5f1b3
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 367fcdae26b66cce06fd6086a21d3212c7ac17ae
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="member-access-operators--and--gt"></a>Operatory dostępu do elementów członkowskich:. i -&gt;
## <a name="syntax"></a>Składnia  
  
```  
postfix-expression . name  
postfix-expression -> name  
```  
  
## <a name="remarks"></a>Uwagi  
 Operatory dostępu do elementu członkowskiego **.** i  **->**  są używane do odwoływania się do elementów członkowskich klasy, Unii i struktur. Wyrażenia dostęp do elementów członkowskich mają wartości i typ wybrany element członkowski.  
  
 Istnieją dwa rodzaje wyrażeń dostępu do elementów członkowskich:  
  
1.  W formularzu pierwszy *wyrażenie przyrostek* reprezentuje wartość struktury, klasy lub typu Unii i *nazwa* nazwy jest członkiem określonej struktury, Unią lub klasy. Wartość operacji jest *nazwa* i jest wartością l-value, jeśli *wyrażenie przyrostek* jest wartością l-value.  
  
2.  W drugiej formy *wyrażenie przyrostek* reprezentuje wskaźnik do struktury, Unią lub klasa, i *nazwa* nazwy jest członkiem określonej struktury, Unią lub klasy. Wartość jest *nazwę* i jest wartością l-value. **->**  Operator wyłuskań wskaźnika. W związku z tym wyrażenia *e*  **->**  `member` i **(\****e***)**.`member` (gdzie *e* reprezentuje wskaźnik) uzyskanie identycznych wyników (z wyjątkiem sytuacji, gdy operatory  **->**  lub  **\***  są przeciążone).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano obu rodzajów operatora dostępu do elementu członkowskiego.  
  
```  
// expre_Selection_Operator.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
struct Date {  
   Date(int i, int j, int k) : day(i), month(j), year(k){}  
   int month;  
   int day;  
   int year;  
};  
  
int main() {  
   Date mydate(1,1,1900);  
   mydate.month = 2;     
   cout  << mydate.month << "/" << mydate.day  
         << "/" << mydate.year << endl;  
  
   Date *mydate2 = new Date(1,1,2000);  
   mydate2->month = 2;  
   cout  << mydate2->month << "/" << mydate2->day  
         << "/" << mydate2->year << endl;  
   delete mydate2;  
}  
```  
  
```Output  
2/1/1900  
2/1/2000  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia przyrostków](../cpp/postfix-expressions.md)   
 [Operatory C++ wbudowanych, priorytet i łączność](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Klasy i struktury](../cpp/classes-and-structs-cpp.md)   
 [Struktura i elementów członkowskich Unii](../c-language/structure-and-union-members.md)