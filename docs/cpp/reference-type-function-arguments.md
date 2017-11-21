---
title: "Argumenty funkcji typu odwołania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- arguments [C++], function
- functions [C++], paramters
- function parameters [C++], reference-type
- function arguments [C++], reference-type
- passing parameters [C++], reference-type arguments
ms.assetid: 0a70e831-9e76-46c0-821d-aeba13d73cc0
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 63eb2b4c7415dc463b38346909bd2b6fd902c332
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="reference-type-function-arguments"></a>Argumenty funkcji typu odwołania
Jest często bardziej wydajne do przekazania odwołania, a nie duże obiekty, do funkcji. Dzięki temu kompilator, aby przekazać adres obiektu przy zachowaniu składni, które będzie używane do dostępu do obiektu. Rozważmy następujący przykład, który używa `Date` struktury:  
  
```  
// reference_type_function_arguments.cpp  
struct Date  
{  
short DayOfWeek;  
short Month;  
short Day;  
short Year;  
};  
  
// Create a Julian date of the form DDDYYYY  
// from a Gregorian date.  
long JulianFromGregorian( Date& GDate )  
{  
static int cDaysInMonth[] = {  
31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31  
   };  
long JDate = 0;  
// Add in days for months already elapsed.  
for ( int i = 0; i < GDate.Month - 1; ++i )  
JDate += cDaysInMonth[i];  
// Add in days for this month.  
JDate += GDate.Day;  
  
// Check for leap year.  
if ( GDate.Year % 100 != 0 && GDate.Year % 4 == 0 )  
JDate++;  
// Add in year.  
JDate *= 10000;  
JDate += GDate.Year;  
  
return JDate;  
}  
  
int main()  
{  
}  
```  
  
 Poprzedni kod pokazuje, że elementy członkowskie struktury przekazywana przez odwołanie, są dostępne przy użyciu operatora wyboru elementu członkowskiego (**.**) zamiast operatora wyboru elementu członkowskiego wskaźnika (**->**).  
  
 Mimo że argumenty przekazane jako typów referencyjnych obserwować składni typów nie będącego wskaźnikiem, zachowują pojedynczy parametr ważne typów wskaźnika: są można modyfikować, chyba że zadeklarowany jako **const**. Nie można zmodyfikować obiektu, ponieważ celem poprzedni kod `GDate`, jest bardziej odpowiednia prototypu funkcji:  
  
```  
long JulianFromGregorian( const Date& GDate );  
```  
  
 To prototyp gwarantuje, że funkcja `JulianFromGregorian` nie zmienia jej argument.  
  
 Dowolnej funkcji prototypowana jako biorąc typu odwołania może akceptować obiektu tego samego typu w tym miejscu, ponieważ nie istnieje konwersja standardowa ze *typename* do *typename*  **&** .  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołania](../cpp/references-cpp.md)