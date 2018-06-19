---
title: hash_multiset — (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_multiset
dev_langs:
- C++
helpviewer_keywords:
- <cliext/hash_set> header [STL/CLR]
- hash_multiset class [STL/CLR]
- <hash_set> header [STL/CLR]
ms.assetid: 8462bd21-6829-4dd3-ac81-c42d6fdf92f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 819dd9835f173c15b23831e32d6c3a207a3d07c8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33138068"
---
# <a name="hashmultiset-stlclr"></a>hash_multiset (STL/CLR)
Klasa szablonu opisuje obiekt, który określa sekwencję zróżnicowanych długość elementów, która ma dostęp dwukierunkowego. Użyj kontenera `hash_multiset` do zarządzania sekwencję elementów jako tablicy skrótów, każdego wpisu tabeli przechowywania dwukierunkowy połączone listy węzłów i w każdym węźle przechowywania jeden element. Wartość każdego elementu jest używany jako klucz porządkowania sekwencji.  
  
 W polu poniżej, opis `GValue` jest taka sama jak `GKey`, który z kolei jest taka sama jak `Key` o ile nie jest typu ref, w którym to przypadku jest `Key^`.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename Key>  
    ref class hash_multiset  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        Microsoft::VisualC::StlClr::IHash<Gkey, GValue>  
    { ..... };  
```  
  
#### <a name="parameters"></a>Parametry  
 Key  
 Typ części klucza elementu w kontrolowanej sekwencji.  
  
## <a name="members"></a>Elementy członkowskie  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|[hash_multiset::const_iterator (STL/CLR)](../dotnet/hash-multiset-const-iterator-stl-clr.md)|Typ iteratora stałego dla kontrolowanej sekwencji.|  
|[hash_multiset::const_reference (STL/CLR)](../dotnet/hash-multiset-const-reference-stl-clr.md)|Typ stałego odwołania do elementu.|  
|[hash_multiset::const_reverse_iterator (STL/CLR)](../dotnet/hash-multiset-const-reverse-iterator-stl-clr.md)|Typ stałej iteratora wstecznego w kontrolowanej sekwencji.|  
|[hash_multiset::difference_type (STL/CLR)](../dotnet/hash-multiset-difference-type-stl-clr.md)|Typ (prawdopodobnie podpisanego) odległość między dwoma elementami.|  
|[hash_multiset::generic_container (STL/CLR)](../dotnet/hash-multiset-generic-container-stl-clr.md)|Typ ogólny interfejs umożliwiający kontenera.|  
|[hash_multiset::generic_iterator (STL/CLR)](../dotnet/hash-multiset-generic-iterator-stl-clr.md)|Typ iteratora dla ogólnego interfejsu do kontenera.|  
|[hash_multiset::generic_reverse_iterator (STL/CLR)](../dotnet/hash-multiset-generic-reverse-iterator-stl-clr.md)|Typ odwrotnej iteratora dla ogólnego interfejsu do kontenera.|  
|[hash_multiset::generic_value (STL/CLR)](../dotnet/hash-multiset-generic-value-stl-clr.md)|Typ elementu dla ogólnego interfejsu do kontenera.|  
|[hash_multiset::hasher (STL/CLR)](../dotnet/hash-multiset-hasher-stl-clr.md)|Delegat funkcji skrótu dla klucza.|  
|[hash_multiset::iterator (STL/CLR)](../dotnet/hash-multiset-iterator-stl-clr.md)|Typ iteratora dla kontrolowanej sekwencji.|  
|[hash_multiset::key_compare (STL/CLR)](../dotnet/hash-multiset-key-compare-stl-clr.md)|Delegat porządkowania dla dwa klucze.|  
|[hash_multiset::key_type (STL/CLR)](../dotnet/hash-multiset-key-type-stl-clr.md)|Typ klucza sortowania.|  
|[hash_multiset::reference (STL/CLR)](../dotnet/hash-multiset-reference-stl-clr.md)|Typ odwołania do elementu.|  
|[hash_multiset::reverse_iterator (STL/CLR)](../dotnet/hash-multiset-reverse-iterator-stl-clr.md)|Typ odwrotnej iteratora w kontrolowanej sekwencji.|  
|[hash_multiset::size_type (STL/CLR)](../dotnet/hash-multiset-size-type-stl-clr.md)|Typ (nieujemną) odległość między dwoma elementami.|  
|[hash_multiset::value_compare (STL/CLR)](../dotnet/hash-multiset-value-compare-stl-clr.md)|Delegat porządkowania dla dwóch wartości elementu.|  
|[hash_multiset::value_type (STL/CLR)](../dotnet/hash-multiset-value-type-stl-clr.md)|Typ elementu.|  
  
|Funkcja elementów członkowskich|Opis|  
|---------------------|-----------------|  
|[hash_multiset::begin (STL/CLR)](../dotnet/hash-multiset-begin-stl-clr.md)|Określa początek kontrolowanej sekwencji.|  
|[hash_multiset::bucket_count (STL/CLR)](../dotnet/hash-multiset-bucket-count-stl-clr.md)|Zlicza zasobników.|  
|[hash_multiset::clear (STL/CLR)](../dotnet/hash-multiset-clear-stl-clr.md)|Usuwa wszystkie elementy.|  
|[hash_multiset::count (STL/CLR)](../dotnet/hash-multiset-count-stl-clr.md)|Liczba elementów pasujących określonego klucza.|  
|[hash_multiset::empty (STL/CLR)](../dotnet/hash-multiset-empty-stl-clr.md)|Sprawdza, czy nie ma żadnych elementów.|  
|[hash_multiset::end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)|Określa koniec kontrolowanej sekwencji.|  
|[hash_multiset::equal_range (STL/CLR)](../dotnet/hash-multiset-equal-range-stl-clr.md)|Wyszukuje zakres, który odpowiada określonemu kluczowi.|  
|[hash_multiset::erase (STL/CLR)](../dotnet/hash-multiset-erase-stl-clr.md)|Usuwa elementy z określonych pozycji.|  
|[hash_multiset::find (STL/CLR)](../dotnet/hash-multiset-find-stl-clr.md)|Wyszukuje element, który odpowiada określonemu kluczowi.|  
|[hash_multiset::hash_delegate (STL/CLR)](../dotnet/hash-multiset-hash-delegate-stl-clr.md)|Kopiuje delegat wyznaczania wartości skrótu z kluczem.|  
|[hash_multiset::hash_multiset (STL/CLR)](../dotnet/hash-multiset-hash-multiset-stl-clr.md)|Konstruuje obiekt kontenera.|  
|[hash_multiset::insert (STL/CLR)](../dotnet/hash-multiset-insert-stl-clr.md)|Dodaje elementy.|  
|[hash_multiset::key_comp (STL/CLR)](../dotnet/hash-multiset-key-comp-stl-clr.md)|Kopiuje porządkowania delegowanie dla dwa klucze.|  
|[hash_multiset::load_factor (STL/CLR)](../dotnet/hash-multiset-load-factor-stl-clr.md)|Oblicza średnią liczbę elementów na przedział.|  
|[hash_multiset::lower_bound (STL/CLR)](../dotnet/hash-multiset-lower-bound-stl-clr.md)|Wyszukuje początek zakresu, który jest zgodny z określonym kluczem.|  
|[hash_multiset::make_value (STL/CLR)](../dotnet/hash-multiset-make-value-stl-clr.md)|Tworzy obiekt wartość.|  
|[hash_multiset::max_load_factor (STL/CLR)](../dotnet/hash-multiset-max-load-factor-stl-clr.md)|Pobiera lub ustawia maksymalną liczbę elementów na przedział.|  
|[hash_multiset::rbegin (STL/CLR)](../dotnet/hash-multiset-rbegin-stl-clr.md)|Określa początek odwróconej kontrolowanej sekwencji.|  
|[hash_multiset::rehash (STL/CLR)](../dotnet/hash-multiset-rehash-stl-clr.md)|Przebudowuje tabelę mieszania.|  
|[hash_multiset::rend (STL/CLR)](../dotnet/hash-multiset-rend-stl-clr.md)|Określa koniec odwróconej kontrolowanej sekwencji.|  
|[hash_multiset::size (STL/CLR)](../dotnet/hash-multiset-size-stl-clr.md)|Liczy liczbę elementów.|  
|[hash_multiset::swap (STL/CLR)](../dotnet/hash-multiset-swap-stl-clr.md)|Zamienia zawartości dwóch kontenerów.|  
|[hash_multiset::to_array (STL/CLR)](../dotnet/hash-multiset-to-array-stl-clr.md)|Kopiuje kontrolowanej sekwencji do nowej tablicy.|  
|[hash_multiset::upper_bound (STL/CLR)](../dotnet/hash-multiset-upper-bound-stl-clr.md)|Wyszukuje koniec zakresu, który jest zgodny z określonym kluczem.|  
|[hash_multiset::value_comp (STL/CLR)](../dotnet/hash-multiset-value-comp-stl-clr.md)|Kopiuje porządkowania delegowanie dla dwóch wartości elementu.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|[hash_multiset::operator= (STL/CLR)](../dotnet/hash-multiset-operator-assign-stl-clr.md)|Zastępuje kontrolowanej sekwencji.|  
  
## <a name="interfaces"></a>Interfejsy  
  
|Interface|Opis|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Zduplikowany obiekt.|  
|<xref:System.Collections.IEnumerable>|Sekwencji za pomocą elementów.|  
|<xref:System.Collections.ICollection>|Obsługa grupy elementów.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Sekwencji za pośrednictwem typu elementów.|  
|<xref:System.Collections.Generic.ICollection%601>|Obsługa grupę elementów typu.|  
|IHash\<klucza, wartość >|Obsługa ogólnego kontenera.|  
  
## <a name="remarks"></a>Uwagi  
 Obiekt przydziela i zwalnia magazynu w sekwencji, które kontroluje jako poszczególne węzły połączonej listy dwukierunkowego. Aby przyśpieszyć dostępu, obiekt przechowuje zróżnicowanych długość tablicy wskaźników do listy (tablicy skrótów) efektywne zarządzanie całą listę sekwencję podlist, lub pakiety w ramach Agreement. Wstawia elementy na zasobnik, który utrzymuje uporządkowanych, zmieniając łącza między węzłami, nigdy nie, kopiując zawartość z jednego węzła do innego. Oznacza to, można wstawiać i usuwanie elementów za darmo, bez zakłóceń pozostałe elementy.  
  
 Obiekt porządkuje każdego zasobnika kontroluje przez wywołanie metody typu obiektu delegowanego przechowywanych [hash_set::key_compare (STL/CLR)](../dotnet/hash-set-key-compare-stl-clr.md). Można określić obiektu delegowanego przechowywanych podczas konstruowania hash_set; Jeśli określisz ma obiektu delegowanego, wartość domyślna to porównanie `operator<=(key_type, key_type)`.  
  
 Dostęp do obiektu delegowanego przechowywanych przez wywołanie funkcji Członkowskich [hash_set::key_comp (STL/CLR)](../dotnet/hash-set-key-comp-stl-clr.md)`()`. Obiekt delegowany musi definiować równoważne kolejności między kluczami typu [hash_set::key_type (STL/CLR)](../dotnet/hash-set-key-type-stl-clr.md). Oznacza to, na dowolne dwa klucze `X` i `Y`:  
  
 `key_comp()(X, Y)` Zwraca wyniku tego samego typu Boolean przy każdym wywołaniu.  
  
 Jeśli `key_comp()(X, Y) && key_comp()(Y, X)` ma wartość true, następnie `X` i `Y` są określane jako mają równoważne porządkowania.  
  
 Reguły porządkowania zachowuje się jak `operator<=(key_type, key_type)`, `operator>=(key_type, key_type)` lub `operator==(key_type, key_type)` definiuje kolejność eqivalent.  
  
 Należy pamiętać, że kontener zagwarantuje tylko elementy którego klucze będą miały równoważne porządkowanie (i które skrót do tej samej wartości całkowitej) to sąsiadujących ze sobą w pojemniku. W odróżnieniu od klasy szablonu [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md), obiekt klasy szablonu `hash_multiset` nie wymaga czy unikatowy kluczy dla wszystkich elementów. (Co najmniej dwa klucze mogą mieć równoważne porządkowania.)  
  
 Obiekt Określa, które zasobnika powinna zawierać klucz porządkowania przez wywołanie metody typu obiektu delegowanego przechowywanych [hash_set::hasher (STL/CLR)](../dotnet/hash-set-hasher-stl-clr.md). Dostęp do tego obiektu przechowywanych przez wywołanie funkcji Członkowskich [hash_set::hash_delegate (STL/CLR)](../dotnet/hash-set-hash-delegate-stl-clr.md) `()` można uzyskać wartość całkowitą, która jest zależna od wartości klucza. Można określić obiektu delegowanego przechowywanych podczas konstruowania hash_set; Jeśli określisz ma obiektu delegowanego, wartość domyślna to funkcja `System::Object::hash_value(key_type)`. Oznacza to, żadnych kluczy `X` i `Y`:  
  
 `hash_delegate()(X)` Zwraca takiego samego wyniku całkowitą przy każdym wywołaniu.  
  
 Jeśli `X` i `Y` mają równoważne określania kolejności, następnie `hash_delegate()(X)` powinien zwrócić takiego samego wyniku całkowitą jako `hash_delegate()(Y)`.  
  
 Każdy element służy jako klucz i wartość. Sekwencja jest reprezentowana w taki sposób, który umożliwia wyszukiwanie, wstawiania i usuwania elementu umownego z liczba operacji, która jest niezależna od liczby elementów w sekwencji (czas stałej)--co najmniej w najlepszym przypadku. Ponadto, wstawianie elementu nie unieważnia iteratorów, a usuwanie elementu unieważnia tylko te iteratory, które wskazują na usunięty element.  
  
 Jeśli wartości skrótu nie są dystrybuowane jednolicie, jednak tablicy skrótów można dwa degeneracji. W extreme — dla funkcji skrótu, która zawsze zwraca tę samą wartość — wyszukiwanie, wstawiania i usuwania są proporcjonalny do liczby elementów w sekwencji (czas liniowej). Kontener usiłują wybierz funkcji skrótu uzasadnione, Zasobnik średniej wielkości, a rozmiar tablicy skrótów (całkowita liczba zasobników), ale możesz zastąpić dowolne z tych opcji. Zobacz na przykład funkcje [hash_set::max_load_factor (STL/CLR)](../dotnet/hash-set-max-load-factor-stl-clr.md) i [hash_set::rehash (STL/CLR)](../dotnet/hash-set-rehash-stl-clr.md).  
  
 Hash_multiset — obsługuje Iteratory dwukierunkowego, co oznacza, że można przejść do sąsiadujących elementów podane iterację wyznacza elementu w kontrolowanej sekwencji. Specjalne węzła głównego odpowiada zwrócony przez iterator [hash_multiset::end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)`()`. Jeśli jest obecny, można zmniejszyć tego iteratora do ostatniego elementu w kontrolowanej sekwencji. Można zwiększyć iteratora hash_multiset, aby osiągnąć węzła głównego, a następnie będzie Porównaj równa `end()`. Ale nie można wyłuskać zwrócony przez iterator `end()`.  
  
 Należy pamiętać, że nie może odwoływać się do elementu hash_multiset bezpośrednio podanej pozycji numeryczny — wymagającego iteratora dostępie swobodnym.  
  
 Hash_multiset iterator przechowuje dojścia do węzła hash_multiset skojarzony, który z kolei przechowuje dojście do jego skojarzony kontenera. Iteratory można użyć tylko w przypadku ich obiekty skojarzone kontenera. Hash_multiset iterator pozostaje ważny tak długo, jak jego węzła hash_multiset skojarzony jest skojarzony z niektórych hash_multiset. Ponadto prawidłowy iteratora jest dereferencable — służy do dostępu lub zmienić wartości elementu ustanowi — tak długo, jak nie jest równa `end()`.  
  
 Wymazywanie lub usunięcie elementu wywołuje destruktor dla jej wartości przechowywanej. Niszczenie kontenera powoduje wymazanie wszystkich elementów. W związku z tym kontenera, której typ elementów jest klasa ref gwarantuje, że żadnych elementów outlive kontenera. Należy jednak pamiętać, że jest kontenerem dojść `not` zniszczyć elementów.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/hash_set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [hash_map — (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_multiset —](../dotnet/hash-multiset-stl-clr.md)   
 [hash_set — (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [mapy (STL/CLR)](../dotnet/map-stl-clr.md)   
 [Zestaw wielokrotny (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [Zestaw wielokrotny (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [Ustaw (STL/CLR)](../dotnet/set-stl-clr.md)   
 [Dokumentacja biblioteki STL/CLR](../dotnet/stl-clr-library-reference.md)