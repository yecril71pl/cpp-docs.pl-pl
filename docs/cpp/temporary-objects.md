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
ms.openlocfilehash: 5523abd0142b8b6dc3a25beb8ca8d113cf5463bc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="temporary-objects"></a>Obiekty tymczasowe
W niektórych przypadkach, konieczne jest utworzenie obiektów tymczasowych przez kompilator. Takie obiekty tymczasowe mogą być utworzone z następujących powodów:  
  
-   Aby zainicjować odwołanie `const` za pomocą inicjatora o typie różniącym się od typu podstawowego inicjowanego odwołania.  
  
-   Aby przechowywać wartość zwracaną przez funkcję, która zwraca typ zdefiniowany przez użytkownika. Takie obiekty tymczasowe są tworzone tylko wtedy, gdy program nie kopiuje wartości zwracanej do obiektu. Na przykład:  
  
    ```  
    UDT Func1();    //  Declare a function that returns a user-defined  
                    //   type.  
  
    ...  
  
    Func1();        //  Call Func1, but discard return value.  
                    //  A temporary object is created to store the return  
                    //   value.  
    ```  
  
     Ponieważ wartość zwracana nie jest kopiowana do innego obiektu, tworzony jest obiekt tymczasowy. Częstszy przypadek tworzenia obiektów tymczasowych występuje w trakcie obliczania wyrażenia, w którym muszą zostać wywołane funkcje przeciążonego operatora. Takie funkcje przeciążonego operatora zwracają typ zdefiniowany przez użytkownika, który często nie jest kopiowany do innego obiektu.  
  
     Rozważ wyrażenie `ComplexResult = Complex1 + Complex2 + Complex3`. Obliczane jest wyrażenie `Complex1 + Complex2`, a wynik jest przechowywany w obiekcie tymczasowym. Następnie, wyrażenie *tymczasowego* `+ Complex3` jest obliczane i wynikiem jest kopiowany do `ComplexResult` (zakładając, że operator przypisania nie jest przeciążony).  
  
-   Aby przechować wynik rzutowania na typ zdefiniowany przez użytkownika. Gdy obiekt danego typu jest jawnie konwertowany na typ zdefiniowany przez użytkownika, nowy obiekt jest konstruowany jako obiekt tymczasowy.  
  
 Obiekty tymczasowe mają okres istnienia zdefiniowany w punkcie utworzenia oraz punkt, w którym są niszczone. Dowolne wyrażenie, które tworzy co najmniej jeden obiekt tymczasowy, ostatecznie niszczy takie obiekty w kolejności odwrotnej do utworzenia. Punkty, w których występuje niszczenie obiektów pokazano w następującej tabeli.  
  
### <a name="destruction-points-for-temporary-objects"></a>Punkty niszczenia obiektów tymczasowych  
  
|Powód utworzenia obiektów tymczasowych|Punkt niszczenia|  
|------------------------------|-----------------------|  
|Wynik obliczania wyrażenia|Wszystkie obiekty tymczasowe, utworzone jako wynik obliczania wyrażenia, są niszczone na końcu instrukcji wyrażenia (to znaczy w średniku) lub na końcu wyrażeń sterujących instrukcji `for`, `if`, `while`, `do` i `switch`.|  
|Inicjowanie odwołań `const`|Jeśli inicjator nie jest l-wartością tego samego typu co inicjowane odwołanie, tworzony jest obiekt tymczasowy o typie podstawowym obiektu i inicjowany za pomocą wyrażenia inicjowania. Obiekt tymczasowy jest niszczony natychmiast po zniszczeniu odwoływanego obiektu z którym jest powiązany.|  
  
