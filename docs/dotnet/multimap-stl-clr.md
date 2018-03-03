---
title: multimap (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::multimap
dev_langs:
- C++
helpviewer_keywords:
- <map> header [STL/CLR]
- <cliext/map> header [STL/CLR]
- multimap class [STL/CLR]
ms.assetid: 3dfe329d-a078-462a-b050-7999ce6110ad
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2c42fc8d71871a70e3a2d3ffa93a78a4e42d2f53
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="multimap-stlclr"></a>multimap (STL/CLR)
Klasa szablonu opisuje obiekt, który określa sekwencję zróżnicowanych długość elementów, która ma dostęp dwukierunkowego. Użyj kontenera `multimap` do zarządzania sekwencję elementów jako drzewo uporządkowanej zrównoważony (prawie) węzły, każdy przechowywania jeden element. Element składa się z kluczem porządkowania sekwencji i zmapowane wartość, która dotyczy jazdy.  
  
 W polu poniżej, opis `GValue` jest taka sama jak:  
  
 `Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`  
  
 gdzie:  
  
 `GKey`jest taka sama jak `Key` o ile nie jest typu ref, w którym to przypadku jest`Key^`  
  
 `GMapped`jest taka sama jak `Mapped` o ile nie jest typu ref, w którym to przypadku jest`Mapped^`  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename Key,  
    typename Mapped>  
    ref class multimap  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        Microsoft::VisualC::StlClr::ITree<Gkey, GValue>  
    { ..... };  
```  
  
#### <a name="parameters"></a>Parametry  
 Key  
 Typ części klucza elementu w kontrolowanej sekwencji.  
  
 zamapowane  
 Typ składnika dodatkowe elementu w kontrolowanej sekwencji.  
  
## <a name="members"></a>Elementy członkowskie  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|[multimap::const_iterator (STL/CLR)](../dotnet/multimap-const-iterator-stl-clr.md)|Typ iteratora stałego dla kontrolowanej sekwencji.|  
|[multimap::const_reference (STL/CLR)](../dotnet/multimap-const-reference-stl-clr.md)|Typ stałego odwołania do elementu.|  
|[multimap::const_reverse_iterator (STL/CLR)](../dotnet/multimap-const-reverse-iterator-stl-clr.md)|Typ stałej iteratora wstecznego w kontrolowanej sekwencji.|  
|[multimap::difference_type (STL/CLR)](../dotnet/multimap-difference-type-stl-clr.md)|Typ (prawdopodobnie podpisanego) odległość między dwoma elementami.|  
|[multimap::generic_container (STL/CLR)](../dotnet/multimap-generic-container-stl-clr.md)|Typ ogólny interfejs umożliwiający kontenera.|  
|[multimap::generic_iterator (STL/CLR)](../dotnet/multimap-generic-iterator-stl-clr.md)|Typ iteratora dla ogólnego interfejsu do kontenera.|  
|[multimap::generic_reverse_iterator (STL/CLR)](../dotnet/multimap-generic-reverse-iterator-stl-clr.md)|Typ odwrotnej iteratora dla ogólnego interfejsu do kontenera.|  
|[multimap::generic_value (STL/CLR)](../dotnet/multimap-generic-value-stl-clr.md)|Typ elementu dla ogólnego interfejsu do kontenera.|  
|[multimap::iterator (STL/CLR)](../dotnet/multimap-iterator-stl-clr.md)|Typ iteratora dla kontrolowanej sekwencji.|  
|[multimap::key_compare (STL/CLR)](../dotnet/multimap-key-compare-stl-clr.md)|Delegat porządkowania dla dwa klucze.|  
|[multimap::key_type (STL/CLR)](../dotnet/multimap-key-type-stl-clr.md)|Typ klucza sortowania.|  
|[multimap::mapped_type (STL/CLR)](../dotnet/multimap-mapped-type-stl-clr.md)|Typ zamapowanych wartość skojarzoną z każdego klucza.|  
|[multimap::reference (STL/CLR)](../dotnet/multimap-reference-stl-clr.md)|Typ odwołania do elementu.|  
|[multimap::reverse_iterator (STL/CLR)](../dotnet/multimap-reverse-iterator-stl-clr.md)|Typ odwrotnej iteratora w kontrolowanej sekwencji.|  
|[multimap::size_type (STL/CLR)](../dotnet/multimap-size-type-stl-clr.md)|Typ (nieujemną) odległość między dwoma elementami.|  
|[multimap::value_compare (STL/CLR)](../dotnet/multimap-value-compare-stl-clr.md)|Delegat porządkowania dla dwóch wartości elementu.|  
|[multimap::value_type (STL/CLR)](../dotnet/multimap-value-type-stl-clr.md)|Typ elementu.|  
  
|Funkcja elementów członkowskich|Opis|  
|---------------------|-----------------|  
|[multimap::begin (STL/CLR)](../dotnet/multimap-begin-stl-clr.md)|Określa początek kontrolowanej sekwencji.|  
|[multimap::clear (STL/CLR)](../dotnet/multimap-clear-stl-clr.md)|Usuwa wszystkie elementy.|  
|[multimap::count (STL/CLR)](../dotnet/multimap-count-stl-clr.md)|Liczba elementów pasujących określonego klucza.|  
|[multimap::empty (STL/CLR)](../dotnet/multimap-empty-stl-clr.md)|Sprawdza, czy nie ma żadnych elementów.|  
|[multimap::end (STL/CLR)](../dotnet/multimap-end-stl-clr.md)|Określa koniec kontrolowanej sekwencji.|  
|[multimap::equal_range (STL/CLR)](../dotnet/multimap-equal-range-stl-clr.md)|Wyszukuje zakres, który odpowiada określonemu kluczowi.|  
|[multimap::erase (STL/CLR)](../dotnet/multimap-erase-stl-clr.md)|Usuwa elementy z określonych pozycji.|  
|[multimap::find (STL/CLR)](../dotnet/multimap-find-stl-clr.md)|Wyszukuje element, który odpowiada określonemu kluczowi.|  
|[multimap::insert (STL/CLR)](../dotnet/multimap-insert-stl-clr.md)|Dodaje elementy.|  
|[multimap::key_comp (STL/CLR)](../dotnet/multimap-key-comp-stl-clr.md)|Kopiuje porządkowania delegowanie dla dwa klucze.|  
|[multimap::lower_bound (STL/CLR)](../dotnet/multimap-lower-bound-stl-clr.md)|Wyszukuje początek zakresu, który jest zgodny z określonym kluczem.|  
|[multimap::make_value (STL/CLR)](../dotnet/multimap-make-value-stl-clr.md)|Tworzy obiekt wartość.|  
|[multimap::multimap (STL/CLR)](../dotnet/multimap-multimap-stl-clr.md)|Konstruuje obiekt kontenera.|  
|[multimap::rbegin (STL/CLR)](../dotnet/multimap-rbegin-stl-clr.md)|Określa początek odwróconej kontrolowanej sekwencji.|  
|[multimap::rend (STL/CLR)](../dotnet/multimap-rend-stl-clr.md)|Określa koniec odwróconej kontrolowanej sekwencji.|  
|[multimap::size (STL/CLR)](../dotnet/multimap-size-stl-clr.md)|Liczy liczbę elementów.|  
|[multimap::swap (STL/CLR)](../dotnet/multimap-swap-stl-clr.md)|Zamienia zawartości dwóch kontenerów.|  
|[multimap::to_array (STL/CLR)](../dotnet/multimap-to-array-stl-clr.md)|Kopiuje kontrolowanej sekwencji do nowej tablicy.|  
|[multimap::upper_bound (STL/CLR)](../dotnet/multimap-upper-bound-stl-clr.md)|Wyszukuje koniec zakresu, który jest zgodny z określonym kluczem.|  
|[multimap::value_comp (STL/CLR)](../dotnet/multimap-value-comp-stl-clr.md)|Kopiuje porządkowania delegowanie dla dwóch wartości elementu.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|[multimap::operator= (STL/CLR)](../dotnet/multimap-operator-assign-stl-clr.md)|Zastępuje kontrolowanej sekwencji.|  
|[operator!= (multimap) (STL/CLR)](../dotnet/operator-inequality-multimap-stl-clr.md)|Określa, czy `multimap` obiekt nie jest równa innej `multimap` obiektu.|  
|[operator< (multimap) (STL/CLR)](../dotnet/operator-less-than-multimap-stl-clr.md)|Określa, czy `multimap` obiekt jest mniejszy niż innego `multimap` obiektu.|  
|[operator<= (multimap) (STL/CLR)](../dotnet/operator-less-or-equal-multimap-stl-clr.md)|Określa, czy `multimap` obiekt jest mniejszy niż lub równy do innego `multimap` obiektu.|  
|[operator== (multimap) (STL/CLR)](../dotnet/operator-equality-multimap-stl-clr.md)|Określa, czy `multimap` obiekt jest taki sam do innego `multimap` obiektu.|  
|[operator> (multimap) (STL/CLR)](../dotnet/operator-greater-than-multimap-stl-clr.md)|Określa, czy `multimap` obiekt jest większy niż innego `multimap` obiektu.|  
|[operator>= (multimap) (STL/CLR)](../dotnet/operator-greater-or-equal-multimap-stl-clr.md)|Określa, czy `multimap` obiektu jest większa lub równa innej `multimap` obiektu.|  
  
## <a name="interfaces"></a>Interfejsy  
  
|Interface|Opis|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Zduplikowany obiekt.|  
|<xref:System.Collections.IEnumerable>|Sekwencji za pomocą elementów.|  
|<xref:System.Collections.ICollection>|Obsługa grupy elementów.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Sekwencji za pośrednictwem typu elementów.|  
|<xref:System.Collections.Generic.ICollection%601>|Obsługa grupę elementów typu.|  
|ITree\<klucza, wartość >|Obsługa ogólnego kontenera.|  
  
## <a name="remarks"></a>Uwagi  
 Obiekt przydziela i zwalnia magazynu w sekwencji, które kontroluje jako poszczególnych węzłach. Elementy do wstawienia w drzewie zrównoważony (prawie) zapewnia uporządkowanych, zmieniając łącza między węzłami, nigdy nie, kopiując zawartość z jednego węzła do innego. Oznacza to, można wstawiać i usuwanie elementów za darmo, bez zakłóceń pozostałe elementy.  
  
 Obiekt porządkuje sekwencji kontroluje przez wywołanie metody typu obiektu delegowanego przechowywanych [multimap::key_compare (STL/CLR)](../dotnet/multimap-key-compare-stl-clr.md). Można określić obiektu delegowanego przechowywanych podczas konstruowania multimap; Jeśli określisz ma obiektu delegowanego, wartość domyślna to porównanie `operator<(key_type, key_type)`. Dostęp do tego obiektu przechowywanych przez wywołanie funkcji Członkowskich [multimap::key_comp (STL/CLR)](../dotnet/multimap-key-comp-stl-clr.md)`()`.  
  
 Obiekt delegowany musi nałożyć strict słabe porządkowanie dla kluczy typu [multimap::key_type (STL/CLR)](../dotnet/multimap-key-type-stl-clr.md). Oznacza to, na dowolne dwa klucze `X` i `Y`:  
  
 `key_comp()(X, Y)`Zwraca wyniku tego samego typu Boolean przy każdym wywołaniu.  
  
 Jeśli `key_comp()(X, Y)` ma wartość true, następnie `key_comp()(Y, X)` musi mieć wartość false.  
  
 Jeśli `key_comp()(X, Y)` ma wartość true, następnie `X` jest nazywany może zostać określona zanim `Y`.  
  
 Jeśli `!key_comp()(X, Y) && !key_comp()(Y, X)` ma wartość true, następnie `X` i `Y` są określane jako mają równoważne porządkowania.  
  
 Dla każdego elementu `X` czy poprzedza `Y` w kontrolowanej sekwencji `key_comp()(Y, X)` ma wartość false. (Dla domyślnego obiektu delegowanego klucze nigdy nie zmniejszenie wartości.) W odróżnieniu od klasy szablonu [mapy (STL/CLR)](../dotnet/map-stl-clr.md), obiekt klasy szablonu `multimap` nie wymaga czy unikatowy kluczy dla wszystkich elementów. (Co najmniej dwa klucze mogą mieć równoważne porządkowania.)  
  
 Każdy element zawiera osobne klucza i wartości mapowane. Sekwencja jest reprezentowana w taki sposób, który zezwala na wyszukiwanie, wstawiania i usuwania dowolnego elementu z liczbą operacji proporcjonalna do logarytmu liczba elementów w sekwencji (czas logarytmicznej). Ponadto, wstawianie elementu nie unieważnia iteratorów, a usuwanie elementu unieważnia tylko te iteratory, które wskazują na usunięty element.  
  
 Multimap obsługuje Iteratory dwukierunkowego, co oznacza, że można przejść do sąsiadujących elementów podane iterację wyznacza elementu w kontrolowanej sekwencji. Specjalne węzła głównego odpowiada zwrócony przez iterator [multimap::end (STL/CLR)](../dotnet/multimap-end-stl-clr.md)`()`. Jeśli jest obecny, można zmniejszyć tego iteratora do ostatniego elementu w kontrolowanej sekwencji. Można zwiększyć multimap — iteratora do węzła głównego, a następnie będzie Porównaj równa `end()`. Ale nie można wyłuskać zwrócony przez iterator `end()`.  
  
 Należy pamiętać, że nie może odwoływać się do elementu multimap — bezpośrednio podanej pozycji numeryczny — wymagającego iteratora dostępie swobodnym.  
  
 Multimap — iteratora przechowuje dojście do jego skojarzony multimap — węzła, który z kolei przechowuje dojście do jego kontenera skojarzone. Iteratory można użyć tylko w przypadku ich obiekty skojarzone kontenera. Multimap — iteratora pozostaje ważny tak długo, jak jego skojarzony multimap — węzeł jest skojarzony z niektórych multimap. Ponadto prawidłowy iteratora jest dereferencable — służy do dostępu lub zmienić wartości elementu ustanowi — tak długo, jak nie jest równa `end()`.  
  
 Wymazywanie lub usunięcie elementu wywołuje destruktor dla jej wartości przechowywanej. Niszczenie kontenera powoduje wymazanie wszystkich elementów. W związku z tym kontenera, której typ elementów jest klasa ref gwarantuje, że żadnych elementów outlive kontenera. Należy jednak pamiętać, że jest kontenerem dojść `not` zniszczyć elementów.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/map >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [hash_map — (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_multimap — (STL/CLR)](../dotnet/hash-multimap-stl-clr.md)   
 [hash_multiset — (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_set — (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [mapy (STL/CLR)](../dotnet/map-stl-clr.md)   
 [Zestaw wielokrotny (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [Ustaw (STL/CLR)](../dotnet/set-stl-clr.md)   
 [Dokumentacja biblioteki STL/CLR](../dotnet/stl-clr-library-reference.md)