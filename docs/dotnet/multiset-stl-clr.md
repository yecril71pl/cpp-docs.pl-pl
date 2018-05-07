---
title: Zestaw wielokrotny (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::multiset
dev_langs:
- C++
helpviewer_keywords:
- <cliext/set> header [STL/CLR]
- <set> header [STL/CLR]
- multiset class [STL/CLR]
ms.assetid: 7c46e2b4-cd88-49b7-a9e6-63ad5ae7feb5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3e01ec2d9c426d6b95b12fe0db9e5a2e328ae1cc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="multiset-stlclr"></a>multiset (STL/CLR)
Klasa szablonu opisuje obiekt, który określa sekwencję zróżnicowanych długość elementów, która ma dostęp dwukierunkowego. Użyj kontenera `multiset` do zarządzania sekwencję elementów jako drzewo uporządkowanej zrównoważony (prawie) węzły, każdy przechowywania jeden element.  
  
 W polu poniżej, opis `GValue` jest taka sama jak `GKey`, który z kolei jest taka sama jak `Key` o ile nie jest typu ref, w którym to przypadku jest `Key^`.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename Key>  
    ref class multiset  
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
|[multiset::const_iterator (STL/CLR)](../dotnet/multiset-const-iterator-stl-clr.md)|Typ iteratora stałego dla kontrolowanej sekwencji.|  
|[multiset::const_reference (STL/CLR)](../dotnet/multiset-const-reference-stl-clr.md)|Typ stałego odwołania do elementu.|  
|[multiset::const_reverse_iterator (STL/CLR)](../dotnet/multiset-const-reverse-iterator-stl-clr.md)|Typ stałej iteratora wstecznego w kontrolowanej sekwencji.|  
|[multiset::difference_type (STL/CLR)](../dotnet/multiset-difference-type-stl-clr.md)|Typ (prawdopodobnie podpisanego) odległość między dwoma elementami.|  
|[multiset::generic_container (STL/CLR)](../dotnet/multiset-generic-container-stl-clr.md)|Typ ogólny interfejs umożliwiający kontenera.|  
|[multiset::generic_iterator (STL/CLR)](../dotnet/multiset-generic-iterator-stl-clr.md)|Typ iteratora dla ogólnego interfejsu do kontenera.|  
|[multiset::generic_reverse_iterator (STL/CLR)](../dotnet/multiset-generic-reverse-iterator-stl-clr.md)|Typ odwrotnej iteratora dla ogólnego interfejsu do kontenera.|  
|[multiset::generic_value (STL/CLR)](../dotnet/multiset-generic-value-stl-clr.md)|Typ elementu dla ogólnego interfejsu do kontenera.|  
|[multiset::iterator (STL/CLR)](../dotnet/multiset-iterator-stl-clr.md)|Typ iteratora dla kontrolowanej sekwencji.|  
|[multiset::key_compare (STL/CLR)](../dotnet/multiset-key-compare-stl-clr.md)|Delegat porządkowania dla dwa klucze.|  
|[multiset::key_type (STL/CLR)](../dotnet/multiset-key-type-stl-clr.md)|Typ klucza sortowania.|  
|[multiset::reference (STL/CLR)](../dotnet/multiset-reference-stl-clr.md)|Typ odwołania do elementu.|  
|[multiset::reverse_iterator (STL/CLR)](../dotnet/multiset-reverse-iterator-stl-clr.md)|Typ odwrotnej iteratora w kontrolowanej sekwencji.|  
|[multiset::size_type (STL/CLR)](../dotnet/multiset-size-type-stl-clr.md)|Typ (nieujemną) odległość między dwoma elementami.|  
|[multiset::value_compare (STL/CLR)](../dotnet/multiset-value-compare-stl-clr.md)|Delegat porządkowania dla dwóch wartości elementu.|  
|[multiset::value_type (STL/CLR)](../dotnet/multiset-value-type-stl-clr.md)|Typ elementu.|  
  
|Funkcja elementów członkowskich|Opis|  
|---------------------|-----------------|  
|[multiset::begin (STL/CLR)](../dotnet/multiset-begin-stl-clr.md)|Określa początek kontrolowanej sekwencji.|  
|[multiset::clear (STL/CLR)](../dotnet/multiset-clear-stl-clr.md)|Usuwa wszystkie elementy.|  
|[multiset::count (STL/CLR)](../dotnet/multiset-count-stl-clr.md)|Liczba elementów pasujących określonego klucza.|  
|[multiset::empty (STL/CLR)](../dotnet/multiset-empty-stl-clr.md)|Sprawdza, czy nie ma żadnych elementów.|  
|[multiset::end (STL/CLR)](../dotnet/multiset-end-stl-clr.md)|Określa koniec kontrolowanej sekwencji.|  
|[multiset::equal_range (STL/CLR)](../dotnet/multiset-equal-range-stl-clr.md)|Wyszukuje zakres, który odpowiada określonemu kluczowi.|  
|[multiset::erase (STL/CLR)](../dotnet/multiset-erase-stl-clr.md)|Usuwa elementy z określonych pozycji.|  
|[multiset::find (STL/CLR)](../dotnet/multiset-find-stl-clr.md)|Wyszukuje element, który odpowiada określonemu kluczowi.|  
|[multiset::insert (STL/CLR)](../dotnet/multiset-insert-stl-clr.md)|Dodaje elementy.|  
|[multiset::key_comp (STL/CLR)](../dotnet/multiset-key-comp-stl-clr.md)|Kopiuje porządkowania delegowanie dla dwa klucze.|  
|[multiset::lower_bound (STL/CLR)](../dotnet/multiset-lower-bound-stl-clr.md)|Wyszukuje początek zakresu, który jest zgodny z określonym kluczem.|  
|[multiset::make_value (STL/CLR)](../dotnet/multiset-make-value-stl-clr.md)|Tworzy obiekt wartość.|  
|[multiset::multiset (STL/CLR)](../dotnet/multiset-multiset-stl-clr.md)|Konstruuje obiekt kontenera.|  
|[multiset::rbegin (STL/CLR)](../dotnet/multiset-rbegin-stl-clr.md)|Określa początek odwróconej kontrolowanej sekwencji.|  
|[multiset::rend (STL/CLR)](../dotnet/multiset-rend-stl-clr.md)|Określa koniec odwróconej kontrolowanej sekwencji.|  
|[multiset::size (STL/CLR)](../dotnet/multiset-size-stl-clr.md)|Liczy liczbę elementów.|  
|[multiset::swap (STL/CLR)](../dotnet/multiset-swap-stl-clr.md)|Zamienia zawartości dwóch kontenerów.|  
|[multiset::to_array (STL/CLR)](../dotnet/multiset-to-array-stl-clr.md)|Kopiuje kontrolowanej sekwencji do nowej tablicy.|  
|[multiset::upper_bound (STL/CLR)](../dotnet/multiset-upper-bound-stl-clr.md)|Wyszukuje koniec zakresu, który jest zgodny z określonym kluczem.|  
|[multiset::value_comp (STL/CLR)](../dotnet/multiset-value-comp-stl-clr.md)|Kopiuje porządkowania delegowanie dla dwóch wartości elementu.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|[multiset::operator= (STL/CLR)](../dotnet/multiset-operator-assign-stl-clr.md)|Zastępuje kontrolowanej sekwencji.|  
|[operator!= (multiset) (STL/CLR)](../dotnet/operator-inequality-multiset-stl-clr.md)|Określa, czy `multiset` obiekt nie jest równa innej `multiset` obiektu.|  
|[operator< (multiset) (STL/CLR)](../dotnet/operator-less-than-multiset-stl-clr.md)|Określa, czy `multiset` obiekt jest mniejszy niż innego `multiset` obiektu.|  
|[operator<= (multiset) (STL/CLR)](../dotnet/operator-less-or-equal-multiset-stl-clr.md)|Określa, czy `multiset` obiekt jest mniejszy niż lub równy do innego `multiset` obiektu.|  
|[operator== (multiset) (STL/CLR)](../dotnet/operator-equality-multiset-stl-clr.md)|Określa, czy `multiset` obiekt jest taki sam do innego `multiset` obiektu.|  
|[operator> (multiset) (STL/CLR)](../dotnet/operator-greater-than-multiset-stl-clr.md)|Określa, czy `multiset` obiekt jest większy niż innego `multiset` obiektu.|  
|[operator>= (multiset) (STL/CLR)](../dotnet/operator-greater-or-equal-multiset-stl-clr.md)|Określa, czy `multiset` obiektu jest większa lub równa innej `multiset` obiektu.|  
  
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
  
 Obiekt porządkuje sekwencji kontroluje przez wywołanie metody typu obiektu delegowanego przechowywanych [multiset::key_compare (STL/CLR)](../dotnet/multiset-key-compare-stl-clr.md). Można określić obiektu delegowanego przechowywanych podczas konstruowania multiset; Jeśli określisz ma obiektu delegowanego, wartość domyślna to porównanie `operator<(key_type, key_type)`. Dostęp do tego obiektu przechowywanych przez wywołanie funkcji Członkowskich [multiset::key_comp (STL/CLR)](../dotnet/multiset-key-comp-stl-clr.md)`()`.  
  
 Obiekt delegowany musi nałożyć strict słabe porządkowanie dla kluczy typu [multiset::key_type (STL/CLR)](../dotnet/multiset-key-type-stl-clr.md). Oznacza to, na dowolne dwa klucze `X` i `Y`:  
  
 `key_comp()(X, Y)` Zwraca wyniku tego samego typu Boolean przy każdym wywołaniu.  
  
 Jeśli `key_comp()(X, Y)` ma wartość true, następnie `key_comp()(Y, X)` musi mieć wartość false.  
  
 Jeśli `key_comp()(X, Y)` ma wartość true, następnie `X` jest nazywany może zostać określona zanim `Y`.  
  
 Jeśli `!key_comp()(X, Y) && !key_comp()(Y, X)` ma wartość true, następnie `X` i `Y` są określane jako mają równoważne porządkowania.  
  
 Dla każdego elementu `X` czy poprzedza `Y` w kontrolowanej sekwencji `key_comp()(Y, X)` ma wartość false. (Dla domyślnego obiektu delegowanego klucze nigdy nie zmniejszenie wartości.) W odróżnieniu od klasy szablonu [Ustaw (STL/CLR)](../dotnet/set-stl-clr.md), obiekt klasy szablonu `multiset` nie wymaga czy unikatowy kluczy dla wszystkich elementów. (Co najmniej dwa klucze mogą mieć równoważne porządkowania.)  
  
 Każdy element służy jako ey i wartość. Sekwencja jest reprezentowana w taki sposób, który zezwala na wyszukiwanie, wstawiania i usuwania dowolnego elementu z liczbą operacji proporcjonalna do logarytmu liczba elementów w sekwencji (czas logarytmicznej). Ponadto, wstawianie elementu nie unieważnia iteratorów, a usuwanie elementu unieważnia tylko te iteratory, które wskazują na usunięty element.  
  
 Zestaw wielokrotny obsługuje Iteratory dwukierunkowego, co oznacza, że można przejść do sąsiadujących elementów podane iterację wyznacza elementu w kontrolowanej sekwencji. Specjalne węzła głównego odpowiada zwrócony przez iterator [multiset::end (STL/CLR)](../dotnet/multiset-end-stl-clr.md)`()`. Jeśli jest obecny, można zmniejszyć tego iteratora do ostatniego elementu w kontrolowanej sekwencji. Można zwiększyć zestawów wielokrotnych iteratora do węzła głównego, a następnie będzie Porównaj równa `end()`. Ale nie można wyłuskać zwrócony przez iterator `end()`.  
  
 Należy pamiętać, że nie może odwoływać się do elementów zestawów wielokrotnych bezpośrednio podanej pozycji numeryczny — wymagającego iteratora dostępie swobodnym.  
  
 Multiset — iteratora przechowuje dojście do jego skojarzony zestawów wielokrotnych węzła, który z kolei przechowuje dojście do jego kontenera skojarzonego. Iteratory można użyć tylko w przypadku ich obiekty skojarzone kontenera. Zestaw wielokrotny iteratora pozostaje ważny tak długo, jak jego multiset — węzeł jest skojarzony z niektórych zestawu wielokrotnego. Ponadto prawidłowy iteratora jest dereferencable — służy do dostępu lub zmienić wartości elementu ustanowi — tak długo, jak nie jest równa `end()`.  
  
 Wymazywanie lub usunięcie elementu wywołuje destruktor dla jej wartości przechowywanej. Niszczenie kontenera powoduje wymazanie wszystkich elementów. W związku z tym kontenera, której typ elementów jest klasa ref gwarantuje, że żadnych elementów outlive kontenera. Należy jednak pamiętać, że jest kontenerem dojść `not` zniszczyć elementów.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [hash_map — (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_multiset — (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_multiset — (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_set — (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [mapy (STL/CLR)](../dotnet/map-stl-clr.md)   
 [Zestaw wielokrotny](../dotnet/multiset-stl-clr.md)   
 [Ustaw (STL/CLR)](../dotnet/set-stl-clr.md)   
 [Dokumentacja biblioteki STL/CLR](../dotnet/stl-clr-library-reference.md)