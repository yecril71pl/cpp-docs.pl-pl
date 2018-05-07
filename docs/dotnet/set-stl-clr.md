---
title: Ustaw (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::set
dev_langs:
- C++
helpviewer_keywords:
- <cliext/set> header [STL/CLR]
- <set> header [STL/CLR]
- set class [STL/CLR]
ms.assetid: 27d3628c-741a-43a7-bef1-5085536f679e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d6a7ebf4d15d85cb43a6f7101c70e444067a3f7b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="set-stlclr"></a>set (STL/CLR)
Klasa szablonu opisuje obiekt, który określa sekwencję zróżnicowanych długość elementów, która ma dostęp dwukierunkowego. Użyj kontenera `set` do zarządzania sekwencję elementów jako drzewo uporządkowanej zrównoważony (prawie) węzły, każdy przechowywania jeden element.  
  
 W polu poniżej, opis `GValue` jest taka sama jak `GKey`, który z kolei jest taka sama jak `Key` o ile nie jest typu ref, w którym to przypadku jest `Key^`.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename Key>  
    ref class set  
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
  
## <a name="members"></a>Elementy członkowskie  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|[set::const_iterator (STL/CLR)](../dotnet/set-const-iterator-stl-clr.md)|Typ iteratora stałego dla kontrolowanej sekwencji.|  
|[set::const_reference (STL/CLR)](../dotnet/set-const-reference-stl-clr.md)|Typ stałego odwołania do elementu.|  
|[set::const_reverse_iterator (STL/CLR)](../dotnet/set-const-reverse-iterator-stl-clr.md)|Typ stałej iteratora wstecznego w kontrolowanej sekwencji.|  
|[set::difference_type (STL/CLR)](../dotnet/set-difference-type-stl-clr.md)|Typ (prawdopodobnie podpisanego) odległość między dwoma elementami.|  
|[set::generic_container (STL/CLR)](../dotnet/set-generic-container-stl-clr.md)|Typ ogólny interfejs umożliwiający kontenera.|  
|[set::generic_iterator (STL/CLR)](../dotnet/set-generic-iterator-stl-clr.md)|Typ iteratora dla ogólnego interfejsu do kontenera.|  
|[set::generic_reverse_iterator (STL/CLR)](../dotnet/set-generic-reverse-iterator-stl-clr.md)|Typ odwrotnej iteratora dla ogólnego interfejsu do kontenera.|  
|[set::generic_value (STL/CLR)](../dotnet/set-generic-value-stl-clr.md)|Typ elementu dla ogólnego interfejsu do kontenera.|  
|[set::iterator (STL/CLR)](../dotnet/set-iterator-stl-clr.md)|Typ iteratora dla kontrolowanej sekwencji.|  
|[set::key_compare (STL/CLR)](../dotnet/set-key-compare-stl-clr.md)|Delegat porządkowania dla dwa klucze.|  
|[set::key_type (STL/CLR)](../dotnet/set-key-type-stl-clr.md)|Typ klucza sortowania.|  
|[set::reference (STL/CLR)](../dotnet/set-reference-stl-clr.md)|Typ odwołania do elementu.|  
|[set::reverse_iterator (STL/CLR)](../dotnet/set-reverse-iterator-stl-clr.md)|Typ odwrotnej iteratora w kontrolowanej sekwencji.|  
|[set::size_type (STL/CLR)](../dotnet/set-size-type-stl-clr.md)|Typ (nieujemną) odległość między dwoma elementami.|  
|[set::value_compare (STL/CLR)](../dotnet/set-value-compare-stl-clr.md)|Delegat porządkowania dla dwóch wartości elementu.|  
|[set::value_type (STL/CLR)](../dotnet/set-value-type-stl-clr.md)|Typ elementu.|  
  
|Funkcja elementów członkowskich|Opis|  
|---------------------|-----------------|  
|[set::begin (STL/CLR)](../dotnet/set-begin-stl-clr.md)|Określa początek kontrolowanej sekwencji.|  
|[set::clear (STL/CLR)](../dotnet/set-clear-stl-clr.md)|Usuwa wszystkie elementy.|  
|[set::count (STL/CLR)](../dotnet/set-count-stl-clr.md)|Liczba elementów pasujących określonego klucza.|  
|[set::empty (STL/CLR)](../dotnet/set-empty-stl-clr.md)|Sprawdza, czy nie ma żadnych elementów.|  
|[set::end (STL/CLR)](../dotnet/set-end-stl-clr.md)|Określa koniec kontrolowanej sekwencji.|  
|[set::equal_range (STL/CLR)](../dotnet/set-equal-range-stl-clr.md)|Wyszukuje zakres, który odpowiada określonemu kluczowi.|  
|[set::erase (STL/CLR)](../dotnet/set-erase-stl-clr.md)|Usuwa elementy z określonych pozycji.|  
|[set::find (STL/CLR)](../dotnet/set-find-stl-clr.md)|Wyszukuje element, który odpowiada określonemu kluczowi.|  
|[set::insert (STL/CLR)](../dotnet/set-insert-stl-clr.md)|Dodaje elementy.|  
|[set::key_comp (STL/CLR)](../dotnet/set-key-comp-stl-clr.md)|Kopiuje porządkowania delegowanie dla dwa klucze.|  
|[set::lower_bound (STL/CLR)](../dotnet/set-lower-bound-stl-clr.md)|Wyszukuje początek zakresu, który jest zgodny z określonym kluczem.|  
|[set::make_value (STL/CLR)](../dotnet/set-make-value-stl-clr.md)|Tworzy obiekt wartość.|  
|[set::rbegin (STL/CLR)](../dotnet/set-rbegin-stl-clr.md)|Określa początek odwróconej kontrolowanej sekwencji.|  
|[set::rend (STL/CLR)](../dotnet/set-rend-stl-clr.md)|Określa koniec odwróconej kontrolowanej sekwencji.|  
|[set::set (STL/CLR)](../dotnet/set-set-stl-clr.md)|Konstruuje obiekt kontenera.|  
|[set::size (STL/CLR)](../dotnet/set-size-stl-clr.md)|Liczy liczbę elementów.|  
|[set::swap (STL/CLR)](../dotnet/set-swap-stl-clr.md)|Zamienia zawartości dwóch kontenerów.|  
|[set::to_array (STL/CLR)](../dotnet/set-to-array-stl-clr.md)|Kopiuje kontrolowanej sekwencji do nowej tablicy.|  
|[set::upper_bound (STL/CLR)](../dotnet/set-upper-bound-stl-clr.md)|Wyszukuje koniec zakresu, który jest zgodny z określonym kluczem.|  
|[set::value_comp (STL/CLR)](../dotnet/set-value-comp-stl-clr.md)|Kopiuje porządkowania delegowanie dla dwóch wartości elementu.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|[set::operator= (STL/CLR)](../dotnet/set-operator-assign-stl-clr.md)|Zastępuje kontrolowanej sekwencji.|  
|[operator!= (set) (STL/CLR)](../dotnet/operator-inequality-set-stl-clr.md)|Określa, czy `set` obiekt nie jest równa innej `set` obiektu.|  
|[operator< (set) (STL/CLR)](../dotnet/operator-less-than-set-stl-clr.md)|Określa, czy `set` obiekt jest mniejszy niż innego `set` obiektu.|  
|[operator<= (set) (STL/CLR)](../dotnet/operator-less-or-equal-set-stl-clr.md)|Określa, czy `set` obiekt jest mniejszy niż lub równy do innego `set` obiektu.|  
|[operator== (set) (STL/CLR)](../dotnet/operator-equality-set-stl-clr.md)|Określa, czy `set` obiekt jest taki sam do innego `set` obiektu.|  
|[operator> (set) (STL/CLR)](../dotnet/operator-greater-than-set-stl-clr.md)|Określa, czy `set` obiekt jest większy niż innego `set` obiektu.|  
|[operator>= (set) (STL/CLR)](../dotnet/operator-greater-or-equal-set-stl-clr.md)|Określa, czy `set` obiektu jest większa lub równa innej `set` obiektu.|  
  
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
  
 Obiekt porządkuje sekwencji kontroluje przez wywołanie metody typu obiektu delegowanego przechowywanych [set::key_compare (STL/CLR)](../dotnet/set-key-compare-stl-clr.md). Można określić obiektu delegowanego przechowywane, podczas tworzenia zestawu; Jeśli określisz ma obiektu delegowanego, wartość domyślna to porównanie `operator<(key_type, key_type)`. Dostęp do tego obiektu przechowywanych przez wywołanie funkcji Członkowskich [set::key_comp (STL/CLR)](../dotnet/set-key-comp-stl-clr.md)`()`.  
  
 Obiekt delegowany musi nałożyć strict słabe porządkowanie dla kluczy typu [set::key_type (STL/CLR)](../dotnet/set-key-type-stl-clr.md). Oznacza to, na dowolne dwa klucze `X` i `Y`:  
  
 `key_comp()(X, Y)` Zwraca wyniku tego samego typu Boolean przy każdym wywołaniu.  
  
 Jeśli `key_comp()(X, Y)` ma wartość true, następnie `key_comp()(Y, X)` musi mieć wartość false.  
  
 Jeśli `key_comp()(X, Y)` ma wartość true, następnie `X` jest nazywany może zostać określona zanim `Y`.  
  
 Jeśli `!key_comp()(X, Y) && !key_comp()(Y, X)` ma wartość true, następnie `X` i `Y` są określane jako mają równoważne porządkowania.  
  
 Dla każdego elementu `X` czy poprzedza `Y` w kontrolowanej sekwencji `key_comp()(Y, X)` ma wartość false. (Dla domyślnego obiektu delegowanego klucze nigdy nie zmniejszenie wartości.) W odróżnieniu od klasy szablonu [ustawić](../dotnet/set-stl-clr.md), obiekt klasy szablonu `set` nie wymaga czy unikatowy kluczy dla wszystkich elementów. (Co najmniej dwa klucze mogą mieć równoważne porządkowania.)  
  
 Każdy element służy jako ey i wartość. Sekwencja jest reprezentowana w taki sposób, który zezwala na wyszukiwanie, wstawiania i usuwania dowolnego elementu z liczbą operacji proporcjonalna do logarytmu liczba elementów w sekwencji (czas logarytmicznej). Ponadto, wstawianie elementu nie unieważnia iteratorów, a usuwanie elementu unieważnia tylko te iteratory, które wskazują na usunięty element.  
  
 Obsługuje zestaw Iteratory dwukierunkowego, co oznacza, że można przejść do sąsiadujących elementów podane iterację wyznacza elementu w kontrolowanej sekwencji. Specjalne węzła głównego odpowiada zwrócony przez iterator [set::end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`. Jeśli jest obecny, można zmniejszyć tego iteratora do ostatniego elementu w kontrolowanej sekwencji. Można zwiększyć iteratora zestaw, do węzła głównego, a następnie będzie Porównaj równa `end()`. Ale nie można wyłuskać zwrócony przez iterator `end()`.  
  
 Należy pamiętać, że nie może odwoływać się do elementu zestawu bezpośrednio podanej pozycji numeryczny — wymagającego iteratora dostępie swobodnym.  
  
 Iterator zestaw przechowuje dojścia do węzła związany jest zestaw, który z kolei przechowuje dojście do jego skojarzony kontenera. Iteratory można użyć tylko w przypadku ich obiekty skojarzone kontenera. Iterator zestaw pozostaje ważny tak długo, jak jego węzła związany jest zestaw jest skojarzony z niektórych zestawu. Ponadto prawidłowy iteratora jest dereferencable — służy do dostępu lub zmienić wartości elementu ustanowi — tak długo, jak nie jest równa `end()`.  
  
 Wymazywanie lub usunięcie elementu wywołuje destruktor dla jej wartości przechowywanej. Niszczenie kontenera powoduje wymazanie wszystkich elementów. W związku z tym kontenera, której typ elementów jest klasa ref gwarantuje, że żadnych elementów outlive kontenera. Należy jednak pamiętać, że jest kontenerem dojść `not` zniszczyć elementów.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [hash_map — (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_set — (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [hash_set — (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [hash_set — (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [mapy (STL/CLR)](../dotnet/map-stl-clr.md)   
 [zestaw](../dotnet/set-stl-clr.md)   
 [zestaw](../dotnet/set-stl-clr.md)   
 [Dokumentacja biblioteki STL/CLR](../dotnet/stl-clr-library-reference.md)