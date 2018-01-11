---
title: "Przykładowy kontener klasy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: container classes [C++]
ms.assetid: 5b1451f2-c708-45da-bbf0-9e42fd687a1a
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3666bf4ee03149a9c00ec93d9fc1dc536ce2d080
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="sample-container-class"></a>Sample Container — Klasa
> [!NOTE]
>  Ten temat dotyczy w dokumentacji Visual C++ prawidłowo przykład kontenerów używanych w standardowej bibliotece C++. Aby uzyskać więcej informacji, zobacz [standardowe kontenery biblioteki C++](../standard-library/stl-containers.md).  
  
 Opisuje obiekt, który kontroluje sekwencji zróżnicowanych długość elementów, zwykle typu **Ty**. Sekwencja jest przechowywany na różne sposoby, w zależności od rzeczywistej kontenera.  
  
 Funkcja konstruktora lub elementu członkowskiego kontenera może się okazać razem, gdy wywołanie konstruktora **Ty**(**const Ty &**) lub funkcja **Ty::operator =**(**const Ty &**). Jeśli takie połączenie zgłasza wyjątek, obiektu kontenera jest zobowiązany do utrzymanie integralności i do ponownego zgłoszenia wyjątku, który przechwytuje go. Można bezpiecznie wymiany, przypisać do wymazać lub zniszczenia obiektu kontenera po zgłasza wyjątek, jeden z tych wyjątków. Ogólnie rzecz biorąc, jednak nie można w przeciwnym razie przewidzieć stan sekwencji kontrolowane przez obiekt kontenera.  
  
 Kilka dodatkowych ostrzeżenia:  
  
-   Jeśli wyrażenie **~ Ty** zwraca wyjątek, Wynikowy stan obiektu kontenera jest niezdefiniowany.  
  
-   Jeśli kontener przechowuje obiekt alokatora *al*, i *al* zgłasza wyjątek innych niż w wyniku wywołania *al***.allocate**, Wynikowy stan obiektu kontenera jest niezdefiniowany.  
  
-   Jeśli kontener przechowuje obiekt funkcji *kompozycji*, aby określić sposób sortowania kontrolowanej sekwencji i *kompozycji* zwraca wyjątek dowolnego rodzaju, Wynikowy stan obiektu kontenera jest niezdefiniowany.  
  
 Klasy kontenerów zdefiniowanych przez standardowa biblioteka C++ spełnić kilka dodatkowych wymagań, zgodnie z opisem w poniższych punktach.  
  
 Kontener szablonu klasy [listy](../standard-library/list-class.md) zapewnia deterministyczna i przydatne, zachowanie nawet w przypadku wystąpienia wyjątków opisanych powyżej. Na przykład jeśli wyjątek podczas wstawiania jednego lub więcej elementów, kontener jest niezmieniony po lewej i jest zgłoszony wyjątek.  
  
 Aby uzyskać *wszystkie* klasy kontenerów zdefiniowanych przez standardowa biblioteka języka C++, jeśli wyjątek podczas wywołania do następujących funkcji Członkowskich:  
  
```  
<A NAME="vclrfcontainerinsert"></A>insert // single element inserted  
<A NAME="vclrfcontainerpushback"></A>push_back  
<A NAME="vclrfcontainerpushfront"></A>push_front  
```  
  
 kontener jest niezmieniony po lewej i jest zgłoszony wyjątek.  
  
 Aby uzyskać *wszystkie* kontenera klas zdefiniowanych w standardowej biblioteki C++, nie jest wyjątek podczas wywołania do następujących funkcji Członkowskich:  
  
```  
<A NAME="vclrfcontainerpopback"></A>pop_back  
<A NAME="vclrfcontainerpopfront"></A>pop_front  
```  
  
 Funkcja członkowska [wymazać](../standard-library/container-class-erase.md) zgłasza wyjątek, tylko wtedy, gdy operacja kopiowania (konstrukcji przypisania lub kopiowania) zgłasza wyjątek.  
  
 Ponadto nie jest wyjątek podczas kopiowania iteratora zwracane przez funkcję elementu członkowskiego.  
  
 Funkcja członkowska [wymiany](../standard-library/container-class-swap.md) sprawia, że dodatkowe ze zobowiązania *wszystkie* kontenera klas zdefiniowanych przez standardowa biblioteka C++:  
  
-   Funkcja członkowska zgłasza wyjątek, tylko wtedy, gdy kontener przechowuje alokatora al obiektu, a `al` zgłasza wyjątek podczas kopiowania.  
  
-   Ważność odwołań, wskaźniki i Iteratory, które określają elementy kontrolowanej sekwencji wymieniane.  
  
 Obiekt klasy kontenera zdefiniowane przez standardowa biblioteka C++ przydziela i zwalnia magazynu na potrzeby sekwencji steruje się za pomocą składowanych obiektu typu `Alloc`, która zwykle jest parametr szablonu. Obiekt alokatora muszą mieć ten sam interfejs zewnętrznych jako obiekt klasy **alokatora\<Ty >**. W szczególności `Alloc` musi być taki sam typ jak **Alloc::rebind < value_type >:: innych**  
  
 Dla *wszystkie* zdefiniowane przez standardowa biblioteka C++, funkcja członkowska klasy kontenerów **get_allocator alokacji stałej;** zwraca kopię obiektu alokatora przechowywane. Należy zauważyć, że obiekt przechowywanych alokatora *nie* kopiowane, gdy jest przypisany obiektu kontenera. Wszystkie konstruktory zainicjować wartości przechowywanej w **alokatora**, do `Alloc` Jeśli brak parametru alokatora zawiera konstruktora.  
  
 Zgodnie z C++ Standard klasę kontenera zdefiniowane przez standardowa biblioteka C++ można założyć, że:  
  
-   Wszystkie obiekty klasy `Alloc` porównania równości.  
  
-   Typ **Alloc::const_pointer** jest taka sama jak **const Ty \*** .  
  
-   Typ **Alloc::const_reference** jest taka sama jak **const Ty &**.  
  
-   Typ **Alloc::pointer** jest taka sama jak **Ty \*** .  
  
-   Typ **Alloc::reference** jest taka sama jak **Ty &**.  
  
 W tej implementacji jednak kontenery nie należy wprowadzać takie założenia. W związku z tym funkcje te działają prawidłowo w alokatora obiektów, które są niższe:  
  
-   Wszystkie obiekty klasy `Alloc` nie trzeba porównać takie same. (Obsługa wielu pul magazynu).  
  
-   Typ **Alloc::const_pointer** nie musi być taka sama jak **const Ty \*** . (Const wskaźnika może być klasą).  
  
-   Typ **Alloc::pointer** nie musi być taka sama jak **Ty \*** . (Wskaźnik może być klasą).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek**: \<przykładowy kontener >  
  
## <a name="see-also"></a>Zobacz też  
 [\<Przykładowy kontener >](../standard-library/sample-container.md)

