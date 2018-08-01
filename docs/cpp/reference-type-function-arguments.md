---
title: Argumenty funkcji typu odwołania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- arguments [C++], function
- functions [C++], paramters
- function parameters [C++], reference-type
- function arguments [C++], reference-type
- passing parameters [C++], reference-type arguments
ms.assetid: 0a70e831-9e76-46c0-821d-aeba13d73cc0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fad8fc85a37aec80d09ed6df9280a78de0540f01
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408606"
---
# <a name="reference-type-function-arguments"></a>Argumenty funkcji typu odwołania
Jest często bardziej wydajnym sposobem przekazywania odwołania, a nie dużych obiektów, do funkcji. Dzięki temu kompilator mógł przekazać adres obiektu, przy zachowaniu składni, która będzie używana do dostępu do obiektu. Rozważmy następujący przykład, który używa `Date` strukturę:  
  
```cpp 
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
  
 Poprzedni kod pokazuje dostępne elementy członkowskie struktury przekazywany przez odwołanie za pomocą operatora wyboru składowej (**.**) zamiast operatora wyboru elementu członkowskiego wskaźnika (**->**).  
  
 Mimo że argumenty przekazane jako typy odwołań, Sprawdź składnię typów nie będącego wskaźnikiem, zachowują jedną z ważnych cech typów wskaźnika: są one można modyfikować, chyba że zadeklarowany jako **const**. Ponieważ celem poprzedni kod nie może modyfikować dany obiekt `GDate`, jest bardziej odpowiednia prototypu funkcji:  
  
```cpp 
long JulianFromGregorian( const Date& GDate );  
```  
  
 Prototyp to gwarantuje, że funkcja `JulianFromGregorian` nie zmieni się z jej argument.  
  
 Dowolnej funkcji prototypowej jako biorąc typu odwołania może zaakceptować obiekt tego samego typu, w tym miejscu, ponieważ nie istnieje konwersja standardowa ze *typename* do * typename ***&**.  
  
## <a name="see-also"></a>Zobacz także  
 [Odwołania](../cpp/references-cpp.md)