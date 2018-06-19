---
title: hash_multimap — (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_multimap
dev_langs:
- C++
helpviewer_keywords:
- hash_multimap class [STL/CLR]
- <cliext/hash_map> header [STL/CLR]
- <hash_map> header [STL/CLR]
ms.assetid: cd78687b-8a05-48e0-9d22-8b8194ae3b0b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 027ed43936e4335819f95d10050de37570e6a679
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33137996"
---
# <a name="hashmultimap-stlclr"></a>hash_multimap (STL/CLR)
Klasa szablonu opisuje obiekt, który określa sekwencję zróżnicowanych długość elementów, która ma dostęp dwukierunkowego. Użyj kontenera `hash_multimap` do zarządzania sekwencję elementów jako tablicy skrótów, każdego wpisu tabeli przechowywania dwukierunkowy połączone listy węzłów i w każdym węźle przechowywania jeden element. Element składa się z kluczem porządkowania sekwencji i zmapowane wartość, która dotyczy jazdy.  
  
 W polu poniżej, opis `GValue` jest taka sama jak:  
  
 `Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`  
  
 gdzie:  
  
 `GKey` jest taka sama jak `Key` o ile nie jest typu ref, w którym to przypadku jest `Key^`  
  
 `GMapped` jest taka sama jak `Mapped` o ile nie jest typu ref, w którym to przypadku jest `Mapped^`  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename Key,  
    typename Mapped>  
    ref class hash_multimap  
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
  
 zamapowane  
 Typ składnika dodatkowe elementu w kontrolowanej sekwencji.  
  
## <a name="members"></a>Elementy członkowskie  
  
|Definicja typu|Opis|  
|---------------------|-----------------|  
|[hash_multimap::const_iterator (STL/CLR)](../dotnet/hash-multimap-const-iterator-stl-clr.md)|Typ iteratora stałego dla kontrolowanej sekwencji.|  
|[hash_multimap::const_reference (STL/CLR)](../dotnet/hash-multimap-const-reference-stl-clr.md)|Typ stałego odwołania do elementu.|  
|[hash_multimap::const_reverse_iterator (STL/CLR)](../dotnet/hash-multimap-const-reverse-iterator-stl-clr.md)|Typ stałej iteratora wstecznego w kontrolowanej sekwencji.|  
|[hash_multimap::difference_type (STL/CLR)](../dotnet/hash-multimap-difference-type-stl-clr.md)|Typ (prawdopodobnie podpisanego) odległość między dwoma elementami.|  
|[hash_multimap::generic_container (STL/CLR)](../dotnet/hash-multimap-generic-container-stl-clr.md)|Typ ogólny interfejs umożliwiający kontenera.|  
|[hash_multimap::generic_iterator (STL/CLR)](../dotnet/hash-multimap-generic-iterator-stl-clr.md)|Typ iteratora dla ogólnego interfejsu do kontenera.|  
|[hash_multimap::generic_reverse_iterator (STL/CLR)](../dotnet/hash-multimap-generic-reverse-iterator-stl-clr.md)|Typ odwrotnej iteratora dla ogólnego interfejsu do kontenera.|  
|[hash_multimap::generic_value (STL/CLR)](../dotnet/hash-multimap-generic-value-stl-clr.md)|Typ elementu dla ogólnego interfejsu do kontenera.|  
|[hash_multimap::hasher (STL/CLR)](../dotnet/hash-multimap-hasher-stl-clr.md)|Delegat funkcji skrótu dla klucza.|  
|[hash_multimap::iterator (STL/CLR)](../dotnet/hash-multimap-iterator-stl-clr.md)|Typ iteratora dla kontrolowanej sekwencji.|  
|[hash_multimap::key_compare (STL/CLR)](../dotnet/hash-multimap-key-compare-stl-clr.md)|Delegat porządkowania dla dwa klucze.|  
|[hash_multimap::key_type (STL/CLR)](../dotnet/hash-multimap-key-type-stl-clr.md)|Typ klucza sortowania.|  
|[hash_multimap::mapped_type (STL/CLR)](../dotnet/hash-multimap-mapped-type-stl-clr.md)|Typ zamapowanych wartość skojarzoną z każdego klucza.|  
|[hash_multimap::reference (STL/CLR)](../dotnet/hash-multimap-reference-stl-clr.md)|Typ odwołania do elementu.|  
|[hash_multimap::reverse_iterator (STL/CLR)](../dotnet/hash-multimap-reverse-iterator-stl-clr.md)|Typ odwrotnej iteratora w kontrolowanej sekwencji.|  
|[hash_multimap::size_type (STL/CLR)](../dotnet/hash-multimap-size-type-stl-clr.md)|Typ (nieujemną) odległość między dwoma elementami.|  
|[hash_multimap::value_compare (STL/CLR)](../dotnet/hash-multimap-value-compare-stl-clr.md)|Delegat porządkowania dla dwóch wartości elementu.|  
|[hash_multimap::value_type (STL/CLR)](../dotnet/hash-multimap-value-type-stl-clr.md)|Typ elementu.|  
  
|Funkcja elementów członkowskich|Opis|  
|---------------------|-----------------|  
|[hash_multimap::begin (STL/CLR)](../dotnet/hash-multimap-begin-stl-clr.md)|Określa początek kontrolowanej sekwencji.|  
|[hash_multimap::bucket_count (STL/CLR)](../dotnet/hash-multimap-bucket-count-stl-clr.md)|Zlicza zasobników.|  
|[hash_multimap::clear (STL/CLR)](../dotnet/hash-multimap-clear-stl-clr.md)|Usuwa wszystkie elementy.|  
|[hash_multimap::count (STL/CLR)](../dotnet/hash-multimap-count-stl-clr.md)|Liczba elementów pasujących określonego klucza.|  
|[hash_multimap::empty (STL/CLR)](../dotnet/hash-multimap-empty-stl-clr.md)|Sprawdza, czy nie ma żadnych elementów.|  
|[hash_multimap::end (STL/CLR)](../dotnet/hash-multimap-end-stl-clr.md)|Określa koniec kontrolowanej sekwencji.|  
|[hash_multimap::equal_range (STL/CLR)](../dotnet/hash-multimap-equal-range-stl-clr.md)|Wyszukuje zakres, który odpowiada określonemu kluczowi.|  
|[hash_multimap::erase (STL/CLR)](../dotnet/hash-multimap-erase-stl-clr.md)|Usuwa elementy z określonych pozycji.|  
|[hash_multimap::find (STL/CLR)](../dotnet/hash-multimap-find-stl-clr.md)|Wyszukuje element, który odpowiada określonemu kluczowi.|  
|[hash_multimap::hash_delegate (STL/CLR)](../dotnet/hash-multimap-hash-delegate-stl-clr.md)|Kopiuje delegat wyznaczania wartości skrótu z kluczem.|  
|[hash_multimap::hash_multimap (STL/CLR)](../dotnet/hash-multimap-hash-multimap-stl-clr.md)|Konstruuje obiekt kontenera.|  
|[hash_multimap::insert (STL/CLR)](../dotnet/hash-multimap-insert-stl-clr.md)|Dodaje elementy.|  
|[hash_multimap::key_comp (STL/CLR)](../dotnet/hash-multimap-key-comp-stl-clr.md)|Kopiuje porządkowania delegowanie dla dwa klucze.|  
|[hash_multimap::load_factor (STL/CLR)](../dotnet/hash-multimap-load-factor-stl-clr.md)|Oblicza średnią liczbę elementów na przedział.|  
|[hash_multimap::lower_bound (STL/CLR)](../dotnet/hash-multimap-lower-bound-stl-clr.md)|Wyszukuje początek zakresu, który jest zgodny z określonym kluczem.|  
|[hash_multimap::make_value (STL/CLR)](../dotnet/hash-multimap-make-value-stl-clr.md)|Tworzy obiekt wartość.|  
|[hash_multimap::max_load_factor (STL/CLR)](../dotnet/hash-multimap-max-load-factor-stl-clr.md)|Pobiera lub ustawia maksymalną liczbę elementów na przedział.|  
|[hash_multimap::rbegin (STL/CLR)](../dotnet/hash-multimap-rbegin-stl-clr.md)|Określa początek odwróconej kontrolowanej sekwencji.|  
|[hash_multimap::rehash (STL/CLR)](../dotnet/hash-multimap-rehash-stl-clr.md)|Przebudowuje tabelę mieszania.|  
|[hash_multimap::rend (STL/CLR)](../dotnet/hash-multimap-rend-stl-clr.md)|Określa koniec odwróconej kontrolowanej sekwencji.|  
|[hash_multimap::size (STL/CLR)](../dotnet/hash-multimap-size-stl-clr.md)|Liczy liczbę elementów.|  
|[hash_multimap::swap (STL/CLR)](../dotnet/hash-multimap-swap-stl-clr.md)|Zamienia zawartości dwóch kontenerów.|  
|[hash_multimap::to_array (STL/CLR)](../dotnet/hash-multimap-to-array-stl-clr.md)|Kopiuje kontrolowanej sekwencji do nowej tablicy.|  
|[hash_multimap::upper_bound (STL/CLR)](../dotnet/hash-multimap-upper-bound-stl-clr.md)|Wyszukuje koniec zakresu, który jest zgodny z określonym kluczem.|  
|[hash_multimap::value_comp (STL/CLR)](../dotnet/hash-multimap-value-comp-stl-clr.md)|Kopiuje porządkowania delegowanie dla dwóch wartości elementu.|  
  
|Operator|Opis|  
|--------------|-----------------|  
|[hash_multimap::operator= (STL/CLR)](../dotnet/hash-multimap-operator-assign-stl-clr.md)|Zastępuje kontrolowanej sekwencji.|  
  
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
  
 Należy pamiętać, że kontener zagwarantuje tylko elementy którego klucze będą miały równoważne porządkowanie (i które skrót do tej samej wartości całkowitej) to sąsiadujących ze sobą w pojemniku. W odróżnieniu od klasy szablonu [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md), obiekt klasy szablonu `hash_multimap` nie wymaga czy unikatowy kluczy dla wszystkich elementów. (Co najmniej dwa klucze mogą mieć równoważne porządkowania.)  
  
 Obiekt Określa, które zasobnika powinna zawierać klucz porządkowania przez wywołanie metody typu obiektu delegowanego przechowywanych [hash_set::hasher (STL/CLR)](../dotnet/hash-set-hasher-stl-clr.md). Dostęp do tego obiektu przechowywanych przez wywołanie funkcji Członkowskich [hash_set::hash_delegate (STL/CLR)](../dotnet/hash-set-hash-delegate-stl-clr.md) `()` można uzyskać wartość całkowitą, która jest zależna od wartości klucza. Można określić obiektu delegowanego przechowywanych podczas konstruowania hash_set; Jeśli określisz ma obiektu delegowanego, wartość domyślna to funkcja `System::Object::hash_value(key_type)`. Oznacza to, żadnych kluczy `X` i `Y`:  
  
 `hash_delegate()(X)` Zwraca takiego samego wyniku całkowitą przy każdym wywołaniu.  
  
 Jeśli `X` i `Y` mają równoważne określania kolejności, następnie `hash_delegate()(X)` powinien zwrócić takiego samego wyniku całkowitą jako `hash_delegate()(Y)`.  
  
 Każdy element zawiera osobne klucza i wartości mapowane. Sekwencja jest reprezentowana w taki sposób, który umożliwia wyszukiwanie, wstawiania i usuwania elementu umownego z liczba operacji, która jest niezależna od liczby elementów w sekwencji (czas stałej)--co najmniej w najlepszym przypadku. Ponadto, wstawianie elementu nie unieważnia iteratorów, a usuwanie elementu unieważnia tylko te iteratory, które wskazują na usunięty element.  
  
 Jeśli wartości skrótu nie są dystrybuowane jednolicie, jednak tablicy skrótów można dwa degeneracji. W extreme — dla funkcji skrótu, która zawsze zwraca tę samą wartość — wyszukiwanie, wstawiania i usuwania są proporcjonalny do liczby elementów w sekwencji (czas liniowej). Kontener usiłują wybierz funkcji skrótu uzasadnione, Zasobnik średniej wielkości, a rozmiar tablicy skrótów (całkowita liczba zasobników), ale możesz zastąpić dowolne z tych opcji. Zobacz na przykład funkcje [hash_set::max_load_factor (STL/CLR)](../dotnet/hash-set-max-load-factor-stl-clr.md) i [hash_set::rehash (STL/CLR)](../dotnet/hash-set-rehash-stl-clr.md).  
  
 Hash_multimap — obsługuje Iteratory dwukierunkowego, co oznacza, że można przejść do sąsiadujących elementów podane iterację wyznacza elementu w kontrolowanej sekwencji. Specjalne węzła głównego odpowiada zwrócony przez iterator [hash_multimap::end (STL/CLR)](../dotnet/hash-multimap-end-stl-clr.md)`()`. Jeśli jest obecny, można zmniejszyć tego iteratora do ostatniego elementu w kontrolowanej sekwencji. Można zwiększyć iteratora hash_multimap, aby osiągnąć węzła głównego, a następnie będzie Porównaj równa `end()`. Ale nie można wyłuskać zwrócony przez iterator `end()`.  
  
 Należy pamiętać, że nie może odwoływać się do elementu hash_multimap bezpośrednio podanej pozycji numeryczny — wymagającego iteratora dostępie swobodnym.  
  
 Hash_multimap iterator przechowuje dojścia do węzła hash_multimap skojarzony, który z kolei przechowuje dojście do jego skojarzony kontenera. Iteratory można użyć tylko w przypadku ich obiekty skojarzone kontenera. Hash_multimap iterator pozostaje ważny tak długo, jak jego węzła hash_multimap skojarzony jest skojarzony z niektórych hash_multimap. Ponadto prawidłowy iteratora jest dereferencable — służy do dostępu lub zmienić wartości elementu ustanowi — tak długo, jak nie jest równa `end()`.  
  
 Wymazywanie lub usunięcie elementu wywołuje destruktor dla jej wartości przechowywanej. Niszczenie kontenera powoduje wymazanie wszystkich elementów. W związku z tym kontenera, której typ elementów jest klasa ref gwarantuje, że żadnych elementów outlive kontenera. Należy jednak pamiętać, że jest kontenerem dojść `not` zniszczyć elementów.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/hash_map >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [hash_map — (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_multiset — (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_set — (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [mapy (STL/CLR)](../dotnet/map-stl-clr.md)   
 [multimap (STL/CLR)](../dotnet/multimap-stl-clr.md)   
 [Zestaw wielokrotny (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [Ustaw (STL/CLR)](../dotnet/set-stl-clr.md)   
 [Dokumentacja biblioteki STL/CLR](../dotnet/stl-clr-library-reference.md)