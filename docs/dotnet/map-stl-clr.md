---
title: mapy (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::map
dev_langs: C++
helpviewer_keywords:
- <map> header [STL/CLR]
- map class [STL/CLR]
- <cliext/map> header [STL/CLR]
ms.assetid: 8b0a7764-b5e4-4175-a802-82b72eb8662a
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6b6e535dac08e473e281f45e45a084d856c931b7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="map-stlclr"></a>map (STL/CLR)
Klasa szablonu opisuje obiekt, który określa sekwencję zróżnicowanych długość elementów, która ma dostęp dwukierunkowego. Użyj kontenera `map` do zarządzania sekwencję elementów jako drzewo uporządkowanej zrównoważony (prawie) węzły, każdy przechowywania jeden element. Element składa się z kluczem porządkowania sekwencji i zmapowane wartość, która dotyczy jazdy.  
  
 W polu poniżej, opis `GValue` jest taka sama jak:  
  
 `Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`  
  
 gdzie:  
  
 `GKey`jest taka sama jak `Key` o ile nie jest typu ref, w którym to przypadku jest`Key^`  
  
 `GMapped`jest taka sama jak `Mapped` o ile nie jest typu ref, w którym to przypadku jest`Mapped^`  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename Key,  
    typename Mapped>  
    ref class map  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        System::Collections::Generic::IDictionary<Gkey, GMapped>,  
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
|[map::const_iterator (STL/CLR)](../dotnet/map-const-iterator-stl-clr.md)|Typ iteratora stałego dla kontrolowanej sekwencji.|  
|[map::const_reference (STL/CLR)](../dotnet/map-const-reference-stl-clr.md)|Typ stałego odwołania do elementu.|  
|[map::const_reverse_iterator (STL/CLR)](../dotnet/map-const-reverse-iterator-stl-clr.md)|Typ stałej iteratora wstecznego w kontrolowanej sekwencji.|  
|[map::difference_type (STL/CLR)](../dotnet/map-difference-type-stl-clr.md)|Typ (prawdopodobnie podpisanego) odległość między dwoma elementami.|  
|[map::generic_container (STL/CLR)](../dotnet/map-generic-container-stl-clr.md)|Typ ogólny interfejs umożliwiający kontenera.|  
|[map::generic_iterator (STL/CLR)](../dotnet/map-generic-iterator-stl-clr.md)|Typ iteratora dla ogólnego interfejsu do kontenera.|  
|[map::generic_reverse_iterator (STL/CLR)](../dotnet/map-generic-reverse-iterator-stl-clr.md)|Typ odwrotnej iteratora dla ogólnego interfejsu do kontenera.|  
|[map::generic_value (STL/CLR)](../dotnet/map-generic-value-stl-clr.md)|Typ elementu dla ogólnego interfejsu do kontenera.|  
|[map::iterator (STL/CLR)](../dotnet/map-iterator-stl-clr.md)|Typ iteratora dla kontrolowanej sekwencji.|  
|[map::key_compare (STL/CLR)](../dotnet/map-key-compare-stl-clr.md)|Delegat porządkowania dla dwa klucze.|  
|[map::key_type (STL/CLR)](../dotnet/map-key-type-stl-clr.md)|Typ klucza sortowania.|  
|[map::mapped_type (STL/CLR)](../dotnet/map-mapped-type-stl-clr.md)|Typ zamapowanych wartość skojarzoną z każdego klucza.|  
|[map::Reference (STL/CLR)](../dotnet/map-reference-stl-clr.md)|Typ odwołania do elementu.|  
|[map::reverse_iterator (STL/CLR)](../dotnet/map-reverse-iterator-stl-clr.md)|Typ odwrotnej iteratora w kontrolowanej sekwencji.|  
|[map::size_type (STL/CLR)](../dotnet/map-size-type-stl-clr.md)|Typ (nieujemną) odległość między dwoma elementami.|  
|[map::value_compare (STL/CLR)](../dotnet/map-value-compare-stl-clr.md)|Delegat porządkowania dla dwóch wartości elementu.|  
|[map::value_type (STL/CLR)](../dotnet/map-value-type-stl-clr.md)|Typ elementu.|  
  
|Funkcja elementów członkowskich|Opis|  
|---------------------|-----------------|  
|[map::BEGIN (STL/CLR)](../dotnet/map-begin-stl-clr.md)|Określa początek kontrolowanej sekwencji.|  
|[map::Clear (STL/CLR)](../dotnet/map-clear-stl-clr.md)|Usuwa wszystkie elementy.|  
|[map::Count (STL/CLR)](../dotnet/map-count-stl-clr.md)|Liczba elementów pasujących określonego klucza.|  
|[map::EMPTY (STL/CLR)](../dotnet/map-empty-stl-clr.md)|Sprawdza, czy nie ma żadnych elementów.|  
|[map::end (STL/CLR)](../dotnet/map-end-stl-clr.md)|Określa koniec kontrolowanej sekwencji.|  
|[map::equal_range (STL/CLR)](../dotnet/map-equal-range-stl-clr.md)|Wyszukuje zakres, który odpowiada określonemu kluczowi.|  
|[map::ERASE (STL/CLR)](../dotnet/map-erase-stl-clr.md)|Usuwa elementy z określonych pozycji.|  
|[map::Find (STL/CLR)](../dotnet/map-find-stl-clr.md)|Wyszukuje element, który odpowiada określonemu kluczowi.|  
|[map::INSERT (STL/CLR)](../dotnet/map-insert-stl-clr.md)|Dodaje elementy.|  
|[map::key_comp (STL/CLR)](../dotnet/map-key-comp-stl-clr.md)|Kopiuje porządkowania delegowanie dla dwa klucze.|  
|[map::lower_bound (STL/CLR)](../dotnet/map-lower-bound-stl-clr.md)|Wyszukuje początek zakresu, który jest zgodny z określonym kluczem.|  
|[map::make_value (STL/CLR)](../dotnet/map-make-value-stl-clr.md)|Tworzy obiekt wartość.|  
|[map::map (STL/CLR)](../dotnet/map-map-stl-clr.md)|Konstruuje obiekt kontenera.|  
|[map::rbegin (STL/CLR)](../dotnet/map-rbegin-stl-clr.md)|Określa początek odwróconej kontrolowanej sekwencji.|  
|[map::rend (STL/CLR)](../dotnet/map-rend-stl-clr.md)|Określa koniec odwróconej kontrolowanej sekwencji.|  
|[map::size (STL/CLR)](../dotnet/map-size-stl-clr.md)|Liczy liczbę elementów.|  
|[map::swap (STL/CLR)](../dotnet/map-swap-stl-clr.md)|Zamienia zawartości dwóch kontenerów.|  
|[map::to_array (STL/CLR)](../dotnet/map-to-array-stl-clr.md)|Kopiuje kontrolowanej sekwencji do nowej tablicy.|  
|[map::upper_bound (STL/CLR)](../dotnet/map-upper-bound-stl-clr.md)|Wyszukuje koniec zakresu, który jest zgodny z określonym kluczem.|  
|[map::value_comp (STL/CLR)](../dotnet/map-value-comp-stl-clr.md)|Kopiuje porządkowania delegowanie dla dwóch wartości elementu.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|[map::operator = (STL/CLR)](../dotnet/map-operator-assign-stl-clr.md)|Zastępuje kontrolowanej sekwencji.|  
|[map::operator(STL/CLR)](../dotnet/map-operator-stl-clr.md)|Mapuje klucz, do jej powiązaną wartość mapowane.|  
|[Operator! = (map) (STL/CLR)](../dotnet/operator-inequality-map-stl-clr.md)|Określa, czy `map` obiekt nie jest równa innej `map` obiektu.|  
|[Operator < (map) (STL/CLR)](../dotnet/operator-less-than-map-stl-clr.md)|Określa, czy `map` obiekt jest mniejszy niż innego `map` obiektu.|  
|[Operator < = (map) (STL/CLR)](../dotnet/operator-less-or-equal-map-stl-clr.md)|Określa, czy `map` obiekt jest mniejszy niż lub równy do innego `map` obiektu.|  
|[Operator == (map) (STL/CLR)](../dotnet/operator-equality-map-stl-clr.md)|Określa, czy `map` obiekt jest taki sam do innego `map` obiektu.|  
|[operator > (map) (STL/CLR)](../dotnet/operator-greater-than-map-stl-clr.md)|Określa, czy `map` obiekt jest większy niż innego `map` obiektu.|  
|[operator > = (map) (STL/CLR)](../dotnet/operator-greater-or-equal-map-stl-clr.md)|Określa, czy `map` obiektu jest większa lub równa innej `map` obiektu.|  
  
## <a name="interfaces"></a>Interfejsy  
  
|Interface|Opis|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Zduplikowany obiekt.|  
|<xref:System.Collections.IEnumerable>|Sekwencji za pomocą elementów.|  
|<xref:System.Collections.ICollection>|Obsługa grupy elementów.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Sekwencji za pośrednictwem typu elementów.|  
|<xref:System.Collections.Generic.ICollection%601>|Obsługa grupę elementów typu.|  
|<xref:System.Collections.Generic.IDictionary%602>|Obsługa grupy {klucza, wartość} pary.|  
|ITree < klucz, wartość >|Obsługa ogólnego kontenera.|  
  
## <a name="remarks"></a>Uwagi  
 Obiekt przydziela i zwalnia magazynu w sekwencji, które kontroluje jako poszczególnych węzłach. Elementy do wstawienia w drzewie zrównoważony (prawie) zapewnia uporządkowanych, zmieniając łącza między węzłami, nigdy nie, kopiując zawartość z jednego węzła do innego. Oznacza to, można wstawiać i usuwanie elementów za darmo, bez zakłóceń pozostałe elementy.  
  
 Obiekt porządkuje sekwencji kontroluje przez wywołanie metody typu obiektu delegowanego przechowywanych [map::key_compare (STL/CLR)](../dotnet/map-key-compare-stl-clr.md). Można określić obiektu delegowanego przechowywanych podczas tworzenia mapy; Jeśli określisz ma obiektu delegowanego, wartość domyślna to porównanie `operator<(key_type, key_type)`. Dostęp do tego obiektu przechowywanych przez wywołanie funkcji Członkowskich [map::key_comp (STL/CLR)](../dotnet/map-key-comp-stl-clr.md)`()`.  
  
 Obiekt delegowany musi nałożyć strict słabe porządkowanie dla kluczy typu [map::key_type (STL/CLR)](../dotnet/map-key-type-stl-clr.md). Oznacza to, na dowolne dwa klucze `X` i `Y`:  
  
 `key_comp()(X, Y)`Zwraca wyniku tego samego typu Boolean przy każdym wywołaniu.  
  
 Jeśli `key_comp()(X, Y)` ma wartość true, następnie `key_comp()(Y, X)` musi mieć wartość false.  
  
 Jeśli `key_comp()(X, Y)` ma wartość true, następnie `X` jest nazywany może zostać określona zanim `Y`.  
  
 Jeśli `!key_comp()(X, Y) && !key_comp()(Y, X)` ma wartość true, następnie `X` i `Y` są określane jako mają równoważne porządkowania.  
  
 Dla każdego elementu `X` czy poprzedza `Y` w kontrolowanej sekwencji `key_comp()(Y, X)` ma wartość false. (Dla domyślnego obiektu delegowanego klucze nigdy nie zmniejszenie wartości.) W odróżnieniu od klasy szablonu [mapy](../dotnet/map-stl-clr.md), obiekt klasy szablonu `map` nie wymaga czy unikatowy kluczy dla wszystkich elementów. (Co najmniej dwa klucze mogą mieć równoważne porządkowania.)  
  
 Każdy element zawiera osobne klucza i wartości mapowane. Sekwencja jest reprezentowana w taki sposób, który zezwala na wyszukiwanie, wstawiania i usuwania dowolnego elementu z liczbą operacji proporcjonalna do logarytmu liczba elementów w sekwencji (czas logarytmicznej). Ponadto, wstawianie elementu nie unieważnia iteratorów, a usuwanie elementu unieważnia tylko te iteratory, które wskazują na usunięty element.  
  
 Mapa obsługuje Iteratory dwukierunkowego, co oznacza, że można przejść do sąsiadujących elementów podane iterację wyznacza elementu w kontrolowanej sekwencji. Specjalne węzła głównego odpowiada zwrócony przez iterator [map::end (STL/CLR)](../dotnet/map-end-stl-clr.md)`()`. Jeśli jest obecny, można zmniejszyć tego iteratora do ostatniego elementu w kontrolowanej sekwencji. Można zwiększyć iteratora mapę, aby osiągnąć węzła głównego, a następnie będzie Porównaj równa `end()`. Ale nie można wyłuskać zwrócony przez iterator `end()`.  
  
 Należy pamiętać, że nie może odwoływać się do elementu mapy bezpośrednio podanej pozycji numeryczny — wymagającego iteratora dostępie swobodnym.  
  
 Iterator mapy przechowuje dojścia do węzła skojarzone mapy, który z kolei przechowuje dojście do jego skojarzony kontenera. Iteratory można użyć tylko w przypadku ich obiekty skojarzone kontenera. Iterator mapy pozostaje ważny tak długo, jak jego węzeł mapy skojarzony jest skojarzony z niektórych mapy. Ponadto prawidłowy iteratora jest dereferencable — służy do dostępu lub zmienić wartości elementu ustanowi — tak długo, jak nie jest równa `end()`.  
  
 Wymazywanie lub usunięcie elementu wywołuje destruktor dla jej wartości przechowywanej. Niszczenie kontenera powoduje wymazanie wszystkich elementów. W związku z tym kontenera, której typ elementów jest klasa ref gwarantuje, że żadnych elementów outlive kontenera. Należy jednak pamiętać, że jest kontenerem dojść `not` zniszczyć elementów.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/map >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [hash_map — (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_map — (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_multiset — (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_set — (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [mapy](../dotnet/map-stl-clr.md)   
 [Zestaw wielokrotny (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [Ustaw (STL/CLR)](../dotnet/set-stl-clr.md)   
 [Odwołanie do biblioteki STL/CLR](../dotnet/stl-clr-library-reference.md)