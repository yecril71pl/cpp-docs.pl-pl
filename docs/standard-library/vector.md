---
title: '&lt;Wektor&gt; | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: <vector>
dev_langs: C++
helpviewer_keywords: vector header
ms.assetid: c1431ad8-c0b6-4dbb-89c4-5f651e432d7f
caps.latest.revision: "25"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0ac628b660c37c4d281c1b889ccf5a3628240573
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ltvectorgt"></a>&lt;Wektor&gt;
Definiuje wektor klasy szablonu kontenera i kilku szablonów pomocniczych.  
  
 `vector` Jest kontenerem, który służy do organizowania elementów danego typu w liniowej sekwencji. Umożliwia szybkie dostępie do elementu i dynamicznego dodawania i usuwania do i z sekwencji. `vector` Jest preferowany kontenera sekwencji, gdy jest dostępie swobodnym wydajności.  
  
 Aby uzyskać więcej informacji o klasie `vector`, zobacz [vector — klasa](../standard-library/vector-class.md). Aby uzyskać informacje o specjalizacji `vector<bool>`, zobacz [wektor\<bool > klasy](../standard-library/vector-bool-class.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
namespace std {  
template <class Type, class Allocator>  
class vector;  
template <class Allocator>  
class vector<bool>;  
 
template <class Allocator>  
struct hash<vector<bool, Allocator>>;  
 // TEMPLATE FUNCTIONS  
template <class Type, class Allocator>  
bool operator== (
    const vector<Type, Allocator>& left,  
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>  
bool operator!= (
    const vector<Type, Allocator>& left,  
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>  
bool operator<(
    const vector<Type, Allocator>& left,  
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>  
bool operator> (
    const vector<Type, Allocator>& left,  
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>  
bool operator<= (
    const vector<Type, Allocator>& left,  
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>  
bool operator>= (
    const vector<Type, Allocator>& left,  
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>  
void swap (
    vector<Type, Allocator>& left,  
    vector<Type, Allocator>& right);

}  // namespace std  
```  
  
#### <a name="parameters"></a>Parametry  
 Typ  
 Parametr szablonu dla typu danych przechowywanych w wektora.  
  
 Program przydzielania  
 Parametr szablonu dla obiektu alokatora przechowywanych odpowiedzialny za alokacji pamięci i cofania alokacji.  
  
 `left`  
 Pierwszy wektora (lewych) w operacji porównywania  
  
 `right`  
 Drugi wektora (po prawej) w operacji porównywania.  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator! =](../standard-library/vector-operators.md#op_neq)|Testy, jeśli obiekt wektora po lewej stronie operatora nie jest taki sam jak obiekt wektora po prawej stronie.|  
|[Operator <](../standard-library/vector-operators.md#op_lt)|Testy, jeśli obiekt wektora po lewej stronie operatora jest mniejsza niż obiekt wektora po prawej stronie.|  
|[operator\<=](../standard-library/vector-operators.md#op_gt_eq)|Testy, jeśli obiekt wektora po lewej stronie operatora jest mniejsza niż lub równe obiekt wektora po prawej stronie.|  
|[operator ==](../standard-library/vector-operators.md#op_eq_eq)|Testy, jeśli obiekt wektora po lewej stronie operatora jest taki sam jak obiekt wektora po prawej stronie.|  
|[operator >](../standard-library/vector-operators.md#op_gt)|Testy, jeśli obiekt wektora po lewej stronie operatora jest większa niż obiekt wektora po prawej stronie.|  
|[operator>=](../standard-library/vector-operators.md#op_gt_eq)|Testy, jeśli obiekt wektora po lewej stronie operatora jest większa niż lub równa obiekt wektora po prawej stronie.|  
  
### <a name="classes"></a>Klasy  
  
|||  
|-|-|  
|[vector, klasa](../standard-library/vector-class.md)|Klasy szablonów sekwencji kontenerów, które Rozmieść elementy danego typu w układzie liniowej i dostęp do szybkiego losowego dowolnego elementu.|  
  
### <a name="specializations"></a>Specjalizacje  
  
|||  
|-|-|  
|[Wektor\<bool > — klasa](../standard-library/vector-bool-class.md)|Pełna specjalizacja wektor klasy szablonu dla elementów typu `bool` z alokatora dla typu źródłowego używane przez specjalizacji.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<wektor >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)

