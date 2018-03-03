---
title: "ATL — klasy zasad kopii | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- data [C++], ATL
- classes [C++], copy policy
- copy policy classes [C++]
- _Copy class
- _CopyInterface class
ms.assetid: 06704b68-d318-4c5d-a65b-71457fe9d00d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 54ac3c9d53c3b6d2b295643001fd15b1e4c6c46d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="atl-copy-policy-classes"></a>Klasy zasad kopii ATL
Kopiowanie zasady klasy są [klasy narzędzi](../atl/utility-classes.md) używany do inicjowania, kopiowanie i usuwanie danych. Klasy zasad kopii pozwalają Aby zdefiniować semantykę kopiowania dla dowolnego typu danych oraz do definiowania konwersje między różnych typów danych.  
  
 Używa kopii zasad klasy ATL w ich implementacji następujące szablony:  
  
-   [CComEnumImpl](../atl/reference/ccomenumimpl-class.md)  
  
-   [IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)  
  
-   [ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)  
  
 Hermetyzując informacje potrzebne do kopiowania lub przekonwertować danych w klasie zasad kopiowania, które mogą być przekazywane jako argument szablonu, deweloperzy ATL zostały podane dla wyjątkową możliwość ponownego wykorzystania tych klas. Na przykład jeśli musisz wdrożyć kolekcji danych dowolnego typu, wystarczy podać jest kopiowania odpowiednich zasad; nigdy nie mają dostępu do kodu, który implementuje kolekcji.  
  
## <a name="definition"></a>Definicja  
 Zgodnie z definicją klasy, która zapewnia następujące funkcje statyczne jest klasą kopiowania zasad:  
  
 `static void init(` `DestinationType` `* p);`  
  
 `static HRESULT copy(` `DestinationType` `* pTo, const`  `SourceType` `* pFrom);`  
  
 `static void destroy(` `DestinationType` `* p);`  
  
 Można zastąpić typy `DestinationType` i *źródłowa* z typami dowolne dane dla każdej zasady kopiowania.  
  
> [!NOTE]
>  Mimo że można zdefiniować klasy zasad kopii dla wszystkich typów dowolne dane, użyj klasy w kodzie ATL należy ograniczyć typy, które sensu. Na przykład, gdy przy użyciu zasad kopii klasy z kolekcji w ATL lub implementacje modułu wyliczającego `DestinationType` musi być typem, który może służyć jako parametru w metodzie interfejsu COM.  
  
 Użyj **init** zainicjować danych, **kopiowania** Aby skopiować dane, i **zniszczyć** zwolnienia danych. Znaczenie inicjowania, kopiowanie i zniszczenie domeny klasy zasad kopii i będą się różnić w zależności od typów danych związane.  
  
 Istnieją dwa wymagania dotyczące użycia i implementacja klasy zasad kopii:  
  
-   Pierwszy parametr **kopiowania** tylko musi otrzymać wskaźnikiem do danych, które zostały wcześniej zainicjowana przy użyciu **init**.  
  
-   **Destroy** tylko musi otrzymać wskaźnikiem do danych, które zostały wcześniej zainicjowana przy użyciu **init** lub kopiowane za pośrednictwem **kopiowania**.  
  
## <a name="standard-implementations"></a>Standardowa implementacji  
 ATL oferuje dwie klasy zasad kopii w formie **_Copy** i **_CopyInterface** szablonu klasy:  
  
-   **_Copy** klasa umożliwia jednorodnych kopiowanie tylko (nie Konwersja typów danych), ponieważ zapewnia ona tylko określić parametr jednego szablonu `DestinationType` i *źródłowa*. Ogólną implementację ten szablon nie zawiera inicjowanie lub niszczenie kodu i używa `memcpy` Aby skopiować dane. ATL udostępnia również specjalizacjach **_Copy** dla **VARIANT**, `LPOLESTR`, **OLEVERB**, i **CONNECTDATA** typów danych.  
  
-   **_CopyInterface** klasa zawiera implementację kopiowanie wskaźniki interfejsu standardowe reguły COM. Ponownie ta klasa umożliwia tylko jednorodnych kopiowania, więc używa przypisanie proste i wywołanie `AddRef` do wykonania kopii.  
  
## <a name="custom-implementations"></a>Implementacje niestandardowe  
 Zazwyczaj należy definiować własne klasy zasad kopii heterogenicznych kopiowania (to znaczy Konwersja typów danych). Niektóre przykłady klas zasady niestandardowe kopiowania przyjrzeć się pliki VCUE_Copy.h i VCUE_CopyString.h w [ATLCollections](../visual-cpp-samples.md) próbki. Te pliki zawierają dwa kopiowania szablonu zasad, klasy `GenericCopy` i `MapCopy`, oraz liczbę specjalizacjach `GenericCopy` dla różnych typów danych.  
  
### <a name="genericcopy"></a>GenericCopy  
 `GenericCopy`Umożliwia określenie *źródłowa* i `DestinationType` jako argumenty szablonu. W tym miejscu jest najbardziej ogólnym formę `GenericCopy` klasy z VCUE_Copy.h:  
  
 [!code-cpp[NVC_ATL_COM#30](../atl/codesnippet/cpp/atl-copy-policy-classes_1.h)]  
  
 VCUE_Copy.h zawiera również następujące specjalizacje tej klasy: `GenericCopy<BSTR>`, `GenericCopy<VARIANT, BSTR>`, `GenericCopy<BSTR, VARIANT>`. VCUE_CopyString.h zawiera specjalizacje kopiowania z **std::string**s: `GenericCopy<std::string>`, `GenericCopy<VARIANT, std::string>`, i `GenericCopy<BSTR, std::string>`. Można zwiększyć `GenericCopy` zapewniając dodatkowe specjalizacje własny.  
  
### <a name="mapcopy"></a>MapCopy  
 `MapCopy`przyjęto założenie, że kopiowane dane są przechowywane w mapie stylu biblioteki C++ Standard, więc umożliwia określenie typu mapy, w którym dane są przechowywane i typu docelowego. Implementacja klasy używa tylko definicje typów dostarczonych przez *MapType* klasy można ustalić typu źródła danych oraz wywołanie odpowiednie `GenericCopy` klasy. Nie są konieczne nie specjalizacje tej klasy.  
  
 [!code-cpp[NVC_ATL_COM#31](../atl/codesnippet/cpp/atl-copy-policy-classes_2.h)]  
  
## <a name="see-also"></a>Zobacz też  
 [Implementowanie kolekcję C++ Standard biblioteki](../atl/implementing-an-stl-based-collection.md)   
 [Przykładowe ATLCollections](../visual-cpp-samples.md)

