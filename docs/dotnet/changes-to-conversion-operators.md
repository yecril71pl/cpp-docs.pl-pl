---
title: "Zmiany operatorów konwersji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- conversion operators
- operators [C++], explicit type conversion
- type conversion, explicit conversions
- conversions, explicit
- explicit keyword [C++]
ms.assetid: 9b83925c-71b7-4bd3-ac2e-843dd7c7f184
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7ab69a7dbba33e37d23a880a6a9b36f7ed37d7d2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="changes-to-conversion-operators"></a>Zmiany operatorów konwersji
Składnia dla operatorów konwersji został zmieniony z rozszerzeń zarządzanych dla języka C++ dla Visual C++.  
  
 Przykładem jest napisanie `op_Implicit` do określenia konwersji. W tym miejscu jest definicją `MyDouble` pobranych z specyfikacja języka:  
  
```  
__gc struct MyDouble {  
   static MyDouble* op_Implicit( int i );   
   static int op_Explicit( MyDouble* val );  
   static String* op_Explicit( MyDouble* val );   
};  
```  
  
 To mówi, że z uwagi całkowitą algorytm konwertowanie tej liczby całkowitej w `MyDouble` są dostarczane przez `op_Implicit` operatora. Ponadto że będzie można przeprowadzić konwersji niejawnie przez kompilator. Podobnie, podane `MyDouble` obiektu, dwa `op_Explicit` operatory podanie odpowiednich algorytmów konwersji obiektu do liczby całkowitej lub zarządzanego `String` jednostki. Jednak kompilator nie będzie wykonywać konwersji, chyba że jawnie żądanej przez użytkownika.  
  
 W języku C# to wygląda następująco:  
  
```  
class MyDouble {  
   public static implicit operator MyDouble( int i );   
   public static explicit operator int( MyDouble val );  
   public static explicit operator string( MyDouble val );   
};  
```  
  
 Kod C# wygląda więcej C++ niż rozszerzeń zarządzanych dla języka C++. To nie jest w przypadku nowej składni.  
  
 Komitetu ISO C++ wprowadzono słowo kluczowe, `explicit`, aby ograniczyć niezamierzone skutki — na przykład `Array` klasa, która przyjmuje jeden argument jako wymiar będzie niejawnie przekonwertować dowolną liczbą całkowitą w `Array` obiekt, który to nie ma. Jednym ze sposobów aby zapobiec takiej sytuacji jest idiom projekt, z fikcyjnymi drugi argument do konstruktora  
  
 Nie należy z drugiej strony, podaj pary konwersji, projektując typu klasy w języku C++. Najlepszy przykład tego jest klasa standardowego ciągu. Niejawna konwersja jest konstruktor jednym argumentem, biorąc ciąg stylu języka C. Jednak nie zawiera odpowiedniego operator niejawnej konwersji — która konwertowania ciągu obiektu na ciąg w stylu języka C, ale raczej wymaga od użytkownika, jawnie Wywołaj funkcję o nazwie — w takim przypadku `c_str()`.  
  
 Tak kojarzenie niejawnej/jawnej zachowanie w operator konwersji (i jako zawierający zestaw konwersje do pojedynczego formularza deklaracji) wydaje się być poprawę oryginalnego obsługi języka C++ w przypadku operatorów konwersji, co ostatecznie prowadzi do `explicit` — słowo kluczowe. Obsługa języka Visual C++ dla operatorów konwersji wygląda następująco, jest nieco mniej szczegółowe niż C# z powodu domyślne zachowanie operatora obsługi aplikacji niejawna konwersja algorytmu:  
  
```  
ref struct MyDouble {  
public:  
   static operator MyDouble^ ( int i );  
   static explicit operator int ( MyDouble^ val );  
   static explicit operator String^ ( MyDouble^ val );  
};  
```  
  
 Inna zmiana jest, że Konstruktor jeden argument jest traktowany tak, jakby jest zadeklarowany jako `explicit`. Oznacza to, że aby wyzwolić jego wywołań, jawnego rzutowania jest wymagane. Należy jednak pamiętać, że jeśli zdefiniowano operator jawnej konwersji i nie konstruktora jednym argumentem została wywołana.  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaracje członków w obrębie klasy lub interfejsu (C + +/ CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)