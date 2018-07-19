---
title: Obiekty tymczasowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- temporary objects
- objects [C++], temporary
ms.assetid: 4c8cec02-391e-4225-9bc6-06d150201412
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2d914b668140f1cbf372e29bcdd4f4b526397fb9
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947758"
---
# <a name="temporary-objects"></a>Obiekty tymczasowe
W niektórych przypadkach, konieczne jest utworzenie obiektów tymczasowych przez kompilator. Takie obiekty tymczasowe mogą być utworzone z następujących powodów:  
  
-   Aby zainicjować **const** odwołanie za pomocą inicjatora o typie różniącym się od tego typu podstawowego inicjowanego odwołania.  
  
-   Aby przechowywać wartość zwracaną przez funkcję, która zwraca typ zdefiniowany przez użytkownika. Takie obiekty tymczasowe są tworzone tylko wtedy, gdy program nie kopiuje wartości zwracanej do obiektu. Na przykład:  
  
    ```cpp 
    UDT Func1();    //  Declare a function that returns a user-defined  
                    //   type.  
  
    ...  
  
    Func1();        //  Call Func1, but discard return value.  
                    //  A temporary object is created to store the return  
                    //   value.  
    ```  
  
     Ponieważ wartość zwracana nie jest kopiowana do innego obiektu, tworzony jest obiekt tymczasowy. Częstszy przypadek tworzenia obiektów tymczasowych występuje w trakcie obliczania wyrażenia, w którym muszą zostać wywołane funkcje przeciążonego operatora. Takie funkcje przeciążonego operatora zwracają typ zdefiniowany przez użytkownika, który często nie jest kopiowany do innego obiektu.  
  
     Rozważ wyrażenie `ComplexResult = Complex1 + Complex2 + Complex3`. Obliczane jest wyrażenie `Complex1 + Complex2`, a wynik jest przechowywany w obiekcie tymczasowym. Następnie, wyrażenie *tymczasowe* `+ Complex3` zostało ocenione, a wynik jest kopiowany do `ComplexResult` (zakładając, że operator przypisania nie jest przeciążony).  
  
-   Aby przechować wynik rzutowania na typ zdefiniowany przez użytkownika. Gdy obiekt danego typu jest jawnie konwertowany na typ zdefiniowany przez użytkownika, nowy obiekt jest konstruowany jako obiekt tymczasowy.  
  
 Obiekty tymczasowe mają okres istnienia zdefiniowany w punkcie utworzenia oraz punkt, w którym są niszczone. Dowolne wyrażenie, które tworzy co najmniej jeden obiekt tymczasowy, ostatecznie niszczy takie obiekty w kolejności odwrotnej do utworzenia. Punkty, w których występuje niszczenie obiektów pokazano w następującej tabeli.  
  
### <a name="destruction-points-for-temporary-objects"></a>Punkty niszczenia obiektów tymczasowych  
  
|Powód utworzenia obiektów tymczasowych|Punkt niszczenia|  
|------------------------------|-----------------------|  
|Wynik obliczania wyrażenia|Wszystkie obiekty tymczasowe, utworzone w wyniku obliczenia wyrażenia są niszczone na końcu instrukcji wyrażenia (to znaczy w średniku), lub na końcu wyrażeń sterujących **dla**, **Jeśli**, **podczas**, **czy**, i **Przełącz** instrukcji.|  
|Inicjowanie **const** odwołania|Jeśli inicjator nie jest l-wartością tego samego typu co inicjowane odwołanie, tworzony jest obiekt tymczasowy o typie podstawowym obiektu i inicjowany za pomocą wyrażenia inicjowania. Obiekt tymczasowy jest niszczony natychmiast po zniszczeniu odwoływanego obiektu z którym jest powiązany.|  
  
