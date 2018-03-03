---
title: "Porady: Tworzenie wystąpień shared_ptr i korzystanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 7d6ebb73-fa0d-4b0b-a528-bf05de96518e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fdabfad3d1b4ae6ee07a8d9e660ab31cbdc1df03
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-create-and-use-sharedptr-instances"></a>Porady: tworzenie wystąpień shared_ptr i korzystanie z nich
Typ `shared_ptr` jest inteligentnym wskaźnikiem w standardowej bibliotece języka C++ przeznaczonym dla scenariuszy, w których więcej niż jeden właściciel może być zmuszony do zarządzania okresem istnienia obiektu w pamięci. Po zainicjowaniu wskaźnika `shared_ptr` można go kopiować, przekazywać wg wartości w argumentach funkcji oraz przypisywać do innych wystąpień wskaźnika `shared_ptr`. Wszystkie wystąpienia wskazują ten sam obiekt oraz mają wspólny dostęp do jednego „bloku sterującego”, który zwiększa i zmniejsza liczbę odwołań po każdym dodaniu nowego wskaźnika `shared_ptr`, wykroczeniu przez wskaźnik poza zakres lub jego zresetowaniu. Gdy licznik odwołań osiągnie zero, blok sterujący usuwa zasób pamięci i samego siebie.  
  
 Na ilustracji poniżej widać kilka wystąpień wskaźnika `shared_ptr`, które wskazują jedną lokalizację w pamięci.  
  
 [![Wskaźnik udostępnionego](../cpp/media/shared_ptr.png "shared_ptr")](assetId:///9785ad08-31d8-411a-86a9-fb9cd9684c27)  
  
## <a name="example"></a>Przykład  
 Jeśli to możliwe, użyj [make_shared —](../standard-library/memory-functions.md#make_shared) funkcja służąca do tworzenia `shared_ptr` utworzenia zasobu pamięci po raz pierwszy. Funkcja `make_shared` jest bezpieczna pod względem wyjątków. Używa tego samego wywołania w celu przydzielenia pamięci blokowi sterującemu i zasobowi, w związku z czym mniej obciąża system podczas konstruowania. Jeśli funkcja `make_shared` nie będzie używana, należy za pomocą jawnego nowego wyrażenia utworzyć obiekt, a następnie przekazać go do konstruktora `shared_ptr`. Poniższy przykład pokazuje różne sposoby deklarowania i inicjowania wskaźnika `shared_ptr` razem z nowym obiektem.  
  
 [!code-cpp[stl_smart_pointers#1](../cpp/codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_1.cpp)]  
  
## <a name="example"></a>Przykład  
 W przykładzie poniżej pokazano sposób deklarowania i inicjowania wystąpień wskaźnika `shared_ptr`, które przyjmują współwłasność obiektu przydzielonego wcześniej przez inny wskaźnik `shared_ptr`. Załóżmy, że zainicjowanym wskaźnikiem `sp2` jest `shared_ptr`.  
  
 [!code-cpp[stl_smart_pointers#2](../cpp/codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_2.cpp)]  
  
## <a name="example"></a>Przykład  
 `shared_ptr`jest również przydatne w kontenerach standardowa biblioteka C++ korzystając z algorytmów kopiowanie elementów. We wskaźniku `shared_ptr` można opakować elementy, po czym skopiować go do innych kontenerów przy założeniu, że bazowa pamięć jest zajęta tylko przez niezbędny czas, nie dłużej. Poniższy przykład pokazuje, jak używać algorytmu `replace_copy_if` do wystąpień wskaźnika `shared_ptr` w wektorze.  
  
 [!code-cpp[stl_smart_pointers#4](../cpp/codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_3.cpp)]  
  
## <a name="example"></a>Przykład  
 Za pomocą funkcji `dynamic_pointer_cast`, `static_pointer_cast` i `const_pointer_cast` można rzutować wskaźnik `shared_ptr`. Funkcje te przypominają operatory `dynamic_cast`, `static_cast` i `const_cast`. W przykładzie poniżej pokazano, jak przetestować typ pochodny każdego elementu w wektorze wskaźnika `shared_ptr` klas bazowych, a następnie skopiować elementy i wyświetlić o nich informacje.  
  
 [!code-cpp[stl_smart_pointers#5](../cpp/codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_4.cpp)]  
  
## <a name="example"></a>Przykład  
 Wskaźnik `shared_ptr` można przekazać do innej funkcji w następujące sposoby:  
  
-   Przekazanie wskaźnika `shared_ptr` wg wartości. Powoduje to wywołanie konstruktora kopiującego, zwiększenie wartości licznika odwołań i przekazanie własności obiektowi wywoływanemu. Operacja w pewnym stopniu obciąża system, co może być odczuwalne przy większej liczbie przekazywanych obiektów `shared_ptr`. Opcji należy używać w przypadku, gdy kontrakt kodu (niejawny lub jawny) między obiektami wywołującym i wywoływanym wymaga, aby obiekt wywoływany był właścicielem.  
  
-   Przekazanie wskaźnika `shared_ptr` wg odwołania lub odwołania stałego. W tym przypadku wartość licznika odwołań nie jest zwiększana, a obiekt wywoływany ma dostęp do wskaźnika tak długo, jak obiekt wywołujący nie wykroczy poza zakres. Alternatywnie obiekt wywoływany może utworzyć wskaźnik `shared_ptr` na podstawie odwołania i w ten sposób stać się współwłaścicielem. Opcji należy używać w sytuacjach, gdy obiekt wywołujący nic nie wie o obiekcie wywoływanym albo kiedy trzeba przekazać wskaźnik `shared_ptr`, ale ze względów wydajnościowych operacje kopiowania są niepożądane.  
  
-   Przekazanie bazowego wskaźnika lub odwołania do bazowego obiektu. Obiekt wywoływany może wtedy używać obiekt, ale nie może być jego współwłaścicielem ani wydłużać jego okresu istnienia. Jeśli obiekt wywoływany tworzy wskaźnik `shared_ptr` z nieprzetworzonego wskaźnika, nowy wskaźnik `shared_ptr` jest niezależny od oryginału i nie steruje bazowym zasobem. Opcję należy stosować w przypadku, gdy kontrakt między obiektami wywołującym i wywoływanym jednoznacznie określa, że obiekt wywołujący zachowuje własność nad okresem istnienia wskaźnika `shared_ptr`.  
  
-   Podejmując decyzję o sposobie przekazania wskaźnika `shared_ptr`, należy ustalić, czy obiekt wywoływany ma być współwłaścicielem bazowego zasobu. „Właściciel” to obiekt lub funkcja, która może utrzymywać istnienie bazowego zasobu tak długo, jak to konieczne. Jeśli obiekt wywołujący ma gwarantować, że obiekt wywoływany może przedłużać okres istnienia wskaźnika poza okres istnienia funkcji, należy użyć pierwszej opcji. Gdy przedłużanie okresu istnienia przez obiekt wywoływany nie ma znaczenia, należy stosować przekazywanie wg odwołania i pozwolić obiektowi wywoływanemu na opcjonalne kopiowanie wskaźnika.  
  
-   Jeśli dostęp do bazowego wskaźnika trzeba zapewnić funkcji pomocnika, a wiadomo, że funkcja pomocnika jedynie użyje wskaźnika i zwróci wartość przed zwróceniem wartości z funkcji wywołującej, nie musi ona być współwłaścicielem bazowego wskaźnika. Potrzebuje tylko dostępu do wskaźnika w trakcie okresu istnienia obiektu wywołującego wskaźnika `shared_ptr`. W tym przypadku można bezpiecznie przekazać wskaźnik `shared_ptr` wg odwołania albo przekazać do bazowego obiektu nieprzetworzony wskaźnik lub odwołanie. Taki sposób przekazania jest nieco korzystniejszy pod względem obciążenia systemu, a dodatkowo może pomóc lepiej wyrazić cele programistyczne.  
  
-   Czasami, na przykład w konstrukcji `std:vector<shared_ptr<T>>`, może być konieczne przekazanie każdego wskaźnika `shared_ptr` do treści wyrażenia lambda lub do nazwanego obiektu funkcji. Jeśli wyrażenie lambda lub funkcja nie przechowuje wskaźnika, należy przekazać wskaźnik `shared_ptr` wg odwołania, tak aby uniknąć wywoływania konstruktora kopiującego dla każdego elementu.    
  
## <a name="example"></a>Przykład  
 W przykładzie poniżej pokazano, jak wskaźnik `shared_ptr` przeciąża różne operatory porównania, aby umożliwić porównywanie wskaźników w pamięci, której właścicielami są wystąpienia wskaźnika `shared_ptr`.  
  
 [!code-cpp[stl_smart_pointers#3](../cpp/codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_6.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wskaźniki inteligentne](../cpp/smart-pointers-modern-cpp.md)