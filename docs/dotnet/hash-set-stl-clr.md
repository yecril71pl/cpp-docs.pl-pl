---
title: "hash_set — (STL/CLR) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::hash_set
dev_langs: C++
helpviewer_keywords:
- <cliext/hash_set> header [STL/CLR]
- hash_set class [STL/CLR]
- <hash_set> header [STL/CLR]
ms.assetid: d110e356-ba3e-4e52-9e2d-d997bf975c96
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 43521d3412c7ca7c1f03896fa7732e24bd6d880b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="hashset-stlclr"></a>hash_set (STL/CLR)
Klasa szablonu opisuje obiekt, który określa sekwencję zróżnicowanych długość elementów, która ma dostęp dwukierunkowego. Użyj kontenera `hash_set` do zarządzania sekwencję elementów jako tablicy skrótów, każdego wpisu tabeli przechowywania dwukierunkowy połączone listy węzłów i w każdym węźle przechowywania jeden element. Wartość każdego elementu jest używany jako klucz porządkowania sekwencji.  
  
 W polu poniżej, opis `GValue` jest taka sama jak `GKey`, który z kolei jest taka sama jak `Key` o ile nie jest typu ref, w którym to przypadku jest `Key^`.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename Key>  
    ref class hash_set  
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
|[hash_set::const_iterator (STL/CLR)](../dotnet/hash-set-const-iterator-stl-clr.md)|Typ iteratora stałego dla kontrolowanej sekwencji.|  
|[hash_set::const_reference (STL/CLR)](../dotnet/hash-set-const-reference-stl-clr.md)|Typ stałego odwołania do elementu.|  
|[hash_set::const_reverse_iterator (STL/CLR)](../dotnet/hash-set-const-reverse-iterator-stl-clr.md)|Typ stałej iteratora wstecznego w kontrolowanej sekwencji.|  
|[hash_set::difference_type (STL/CLR)](../dotnet/hash-set-difference-type-stl-clr.md)|Typ (prawdopodobnie podpisanego) odległość między dwoma elementami.|  
|[hash_set::generic_container (STL/CLR)](../dotnet/hash-set-generic-container-stl-clr.md)|Typ ogólny interfejs umożliwiający kontenera.|  
|[hash_set::generic_iterator (STL/CLR)](../dotnet/hash-set-generic-iterator-stl-clr.md)|Typ iteratora dla ogólnego interfejsu do kontenera.|  
|[hash_set::generic_reverse_iterator (STL/CLR)](../dotnet/hash-set-generic-reverse-iterator-stl-clr.md)|Typ odwrotnej iteratora dla ogólnego interfejsu do kontenera.|  
|[hash_set::generic_value (STL/CLR)](../dotnet/hash-set-generic-value-stl-clr.md)|Typ elementu dla ogólnego interfejsu do kontenera.|  
|[hash_set::hasher (STL/CLR)](../dotnet/hash-set-hasher-stl-clr.md)|Delegat funkcji skrótu dla klucza.|  
|[hash_set::iterator (STL/CLR)](../dotnet/hash-set-iterator-stl-clr.md)|Typ iteratora dla kontrolowanej sekwencji.|  
|[hash_set::key_compare (STL/CLR)](../dotnet/hash-set-key-compare-stl-clr.md)|Delegat porządkowania dla dwa klucze.|  
|[hash_set::key_type (STL/CLR)](../dotnet/hash-set-key-type-stl-clr.md)|Typ klucza sortowania.|  
|[hash_set::Reference (STL/CLR)](../dotnet/hash-set-reference-stl-clr.md)|Typ odwołania do elementu.|  
|[hash_set::reverse_iterator (STL/CLR)](../dotnet/hash-set-reverse-iterator-stl-clr.md)|Typ odwrotnej iteratora w kontrolowanej sekwencji.|  
|[hash_set::size_type (STL/CLR)](../dotnet/hash-set-size-type-stl-clr.md)|Typ (nieujemną) odległość między dwoma elementami.|  
|[hash_set::value_compare (STL/CLR)](../dotnet/hash-set-value-compare-stl-clr.md)|Delegat porządkowania dla dwóch wartości elementu.|  
|[hash_set::value_type (STL/CLR)](../dotnet/hash-set-value-type-stl-clr.md)|Typ elementu.|  
  
|Funkcja elementów członkowskich|Opis|  
|---------------------|-----------------|  
|[hash_set::BEGIN (STL/CLR)](../dotnet/hash-set-begin-stl-clr.md)|Określa początek kontrolowanej sekwencji.|  
|[hash_set::bucket_count (STL/CLR)](../dotnet/hash-set-bucket-count-stl-clr.md)|Zlicza zasobników.|  
|[hash_set::Clear (STL/CLR)](../dotnet/hash-set-clear-stl-clr.md)|Usuwa wszystkie elementy.|  
|[hash_set::Count (STL/CLR)](../dotnet/hash-set-count-stl-clr.md)|Liczba elementów pasujących określonego klucza.|  
|[hash_set::EMPTY (STL/CLR)](../dotnet/hash-set-empty-stl-clr.md)|Sprawdza, czy nie ma żadnych elementów.|  
|[hash_set::end (STL/CLR)](../dotnet/hash-set-end-stl-clr.md)|Określa koniec kontrolowanej sekwencji.|  
|[hash_set::equal_range (STL/CLR)](../dotnet/hash-set-equal-range-stl-clr.md)|Wyszukuje zakres, który odpowiada określonemu kluczowi.|  
|[hash_set::ERASE (STL/CLR)](../dotnet/hash-set-erase-stl-clr.md)|Usuwa elementy z określonych pozycji.|  
|[hash_set::Find (STL/CLR)](../dotnet/hash-set-find-stl-clr.md)|Wyszukuje element, który odpowiada określonemu kluczowi.|  
|[hash_set::hash_delegate (STL/CLR)](../dotnet/hash-set-hash-delegate-stl-clr.md)|Kopiuje delegat wyznaczania wartości skrótu z kluczem.|  
|[hash_set::hash_set (STL/CLR)](../dotnet/hash-set-hash-set-stl-clr.md)|Konstruuje obiekt kontenera.|  
|[hash_set::INSERT (STL/CLR)](../dotnet/hash-set-insert-stl-clr.md)|Dodaje elementy.|  
|[hash_set::key_comp (STL/CLR)](../dotnet/hash-set-key-comp-stl-clr.md)|Kopiuje porządkowania delegowanie dla dwa klucze.|  
|[hash_set::load_factor (STL/CLR)](../dotnet/hash-set-load-factor-stl-clr.md)|Oblicza średnią liczbę elementów na przedział.|  
|[hash_set::lower_bound (STL/CLR)](../dotnet/hash-set-lower-bound-stl-clr.md)|Wyszukuje początek zakresu, który jest zgodny z określonym kluczem.|  
|[hash_set::make_value (STL/CLR)](../dotnet/hash-set-make-value-stl-clr.md)|Tworzy obiekt wartość.|  
|[hash_set::max_load_factor (STL/CLR)](../dotnet/hash-set-max-load-factor-stl-clr.md)|Pobiera lub ustawia maksymalną liczbę elementów na przedział.|  
|[hash_set::rbegin (STL/CLR)](../dotnet/hash-set-rbegin-stl-clr.md)|Określa początek odwróconej kontrolowanej sekwencji.|  
|[hash_set::rehash (STL/CLR)](../dotnet/hash-set-rehash-stl-clr.md)|Przebudowuje tabelę mieszania.|  
|[hash_set::rend (STL/CLR)](../dotnet/hash-set-rend-stl-clr.md)|Określa koniec odwróconej kontrolowanej sekwencji.|  
|[hash_set::size (STL/CLR)](../dotnet/hash-set-size-stl-clr.md)|Liczy liczbę elementów.|  
|[hash_set::swap (STL/CLR)](../dotnet/hash-set-swap-stl-clr.md)|Zamienia zawartości dwóch kontenerów.|  
|[hash_set::to_array (STL/CLR)](../dotnet/hash-set-to-array-stl-clr.md)|Kopiuje kontrolowanej sekwencji do nowej tablicy.|  
|[hash_set::upper_bound (STL/CLR)](../dotnet/hash-set-upper-bound-stl-clr.md)|Wyszukuje koniec zakresu, który jest zgodny z określonym kluczem.|  
|[hash_set::value_comp (STL/CLR)](../dotnet/hash-set-value-comp-stl-clr.md)|Kopiuje porządkowania delegowanie dla dwóch wartości elementu.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|[hash_set::operator = (STL/CLR)](../dotnet/hash-set-operator-assign-stl-clr.md)|Zastępuje kontrolowanej sekwencji.|  
  
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
  
 `key_comp()(X, Y)`Zwraca wyniku tego samego typu Boolean przy każdym wywołaniu.  
  
 Jeśli `key_comp()(X, Y) && key_comp()(Y, X)` ma wartość true, następnie `X` i `Y` są określane jako mają równoważne porządkowania.  
  
 Reguły porządkowania zachowuje się jak `operator<=(key_type, key_type)`, `operator>=(key_type, key_type)` lub `operator==(key_type, key_type)` definiuje kolejność eqivalent.  
  
 Należy pamiętać, że kontener zagwarantuje tylko elementy którego klucze będą miały równoważne porządkowanie (i które skrót do tej samej wartości całkowitej) to sąsiadujących ze sobą w pojemniku. W odróżnieniu od klasy szablonu [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md), obiekt klasy szablonu `hash_set` zagwarantuje to unikatowy kluczy dla wszystkich elementów. (Nie dwa klucze jest równoważne kolejności).  
  
 Obiekt Określa, które zasobnika powinna zawierać klucz porządkowania przez wywołanie metody typu obiektu delegowanego przechowywanych [hash_set::hasher (STL/CLR)](../dotnet/hash-set-hasher-stl-clr.md). Dostęp do tego obiektu przechowywanych przez wywołanie funkcji Członkowskich [hash_set::hash_delegate (STL/CLR)](../dotnet/hash-set-hash-delegate-stl-clr.md) `()` można uzyskać wartość całkowitą, która jest zależna od wartości klucza. Można określić obiektu delegowanego przechowywanych podczas konstruowania hash_set; Jeśli określisz ma obiektu delegowanego, wartość domyślna to funkcja `System::Object::hash_value(key_type)`. Oznacza to, żadnych kluczy `X` i `Y`:  
  
 `hash_delegate()(X)`Zwraca takiego samego wyniku całkowitą przy każdym wywołaniu.  
  
 Jeśli `X` i `Y` mają równoważne określania kolejności, następnie `hash_delegate()(X)` powinien zwrócić takiego samego wyniku całkowitą jako `hash_delegate()(Y)`.  
  
 Każdy element służy jako klucz i wartość. Sekwencja jest reprezentowana w taki sposób, który umożliwia wyszukiwanie, wstawiania i usuwania elementu umownego z liczba operacji, która jest niezależna od liczby elementów w sekwencji (czas stałej)--co najmniej w najlepszym przypadku. Ponadto, wstawianie elementu nie unieważnia iteratorów, a usuwanie elementu unieważnia tylko te iteratory, które wskazują na usunięty element.  
  
 Jeśli wartości skrótu nie są dystrybuowane jednolicie, jednak tablicy skrótów można dwa degeneracji. W extreme — dla funkcji skrótu, która zawsze zwraca tę samą wartość — wyszukiwanie, wstawiania i usuwania są proporcjonalny do liczby elementów w sekwencji (czas liniowej). Kontener usiłują wybierz funkcji skrótu uzasadnione, Zasobnik średniej wielkości, a rozmiar tablicy skrótów (całkowita liczba zasobników), ale możesz zastąpić dowolne z tych opcji. Zobacz na przykład funkcje [hash_set::max_load_factor (STL/CLR)](../dotnet/hash-set-max-load-factor-stl-clr.md) i [hash_set::rehash (STL/CLR)](../dotnet/hash-set-rehash-stl-clr.md).  
  
 Hash_set — obsługuje Iteratory dwukierunkowego, co oznacza, że można przejść do sąsiadujących elementów podane iterację wyznacza elementu w kontrolowanej sekwencji. Specjalne węzła głównego odpowiada zwrócony przez iterator [hash_set::end (STL/CLR)](../dotnet/hash-set-end-stl-clr.md)`()`. Jeśli jest obecny, można zmniejszyć tego iteratora do ostatniego elementu w kontrolowanej sekwencji. Można zwiększyć iteratora hash_set, aby osiągnąć węzła głównego, a następnie będzie Porównaj równa `end()`. Ale nie można wyłuskać zwrócony przez iterator `end()`.  
  
 Należy pamiętać, że nie może odwoływać się do elementu hash_set bezpośrednio podanej pozycji numeryczny — wymagającego iteratora dostępie swobodnym.  
  
 Hash_set iterator przechowuje dojścia do węzła hash_set skojarzony, który z kolei przechowuje dojście do jego skojarzony kontenera. Iteratory można użyć tylko w przypadku ich obiekty skojarzone kontenera. Hash_set iterator pozostaje ważny tak długo, jak jego węzła hash_set skojarzony jest skojarzony z niektórych hash_set. Ponadto prawidłowy iteratora jest dereferencable — służy do dostępu lub zmienić wartości elementu ustanowi — tak długo, jak nie jest równa `end()`.  
  
 Wymazywanie lub usunięcie elementu wywołuje destruktor dla jej wartości przechowywanej. Niszczenie kontenera powoduje wymazanie wszystkich elementów. W związku z tym kontenera, której typ elementów jest klasa ref gwarantuje, że żadnych elementów outlive kontenera. Należy jednak pamiętać, że jest kontenerem dojść `not` zniszczyć elementów.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/hash_set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [hash_map — (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_set —](../dotnet/hash-set-stl-clr.md)   
 [hash_set —](../dotnet/hash-set-stl-clr.md)   
 [mapy (STL/CLR)](../dotnet/map-stl-clr.md)   
 [Ustaw (STL/CLR)](../dotnet/set-stl-clr.md)   
 [Ustaw (STL/CLR)](../dotnet/set-stl-clr.md)   
 [Ustaw (STL/CLR)](../dotnet/set-stl-clr.md)   
 [Odwołanie do biblioteki STL/CLR](../dotnet/stl-clr-library-reference.md)