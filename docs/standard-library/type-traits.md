---
title: '&lt;type_traits&gt;'
ms.date: 02/21/2019
f1_keywords:
- <type_traits>
helpviewer_keywords:
- typetrait header
- type_traits
ms.assetid: 2260b51f-8160-4c66-a82f-00b534cb60d4
ms.openlocfilehash: 42c94daf331fd9a17e050067e4c4e495af180b0c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841704"
---
# <a name="lttype_traitsgt"></a>&lt;type_traits&gt;

Definiuje szablony dla stałych czasu kompilacji, które zawierają informacje o właściwościach ich argumentów typu lub generują przekształcone typy.

## <a name="syntax"></a>Składnia

```cpp
#include <type_traits>
```

## <a name="remarks"></a>Uwagi

Klasy i szablony w programie służą \<type_traits> do obsługi wnioskowania o typie, klasyfikacji i transformacji w czasie kompilacji. Są one również używane do wykrywania błędów związanych z typem i pomagają zoptymalizować kod generyczny. Cechy typu jednoargumentowego opisują właściwość typu, cechy typu binarnego opisują relację między typami, a cechy transformacji modyfikują właściwość typu.

Klasa pomocnika `integral_constant` i jej specjalizacje szablonu `true_type` i `false_type` tworzą klasy bazowe dla predykatów typu. *Predykat typu* jest szablonem, który przyjmuje jeden lub więcej argumentów typu. Gdy predykat typu *ma wartość true*, jest publicznie pochodny, bezpośrednio lub pośrednio, z [true_type](../standard-library/type-traits-typedefs.md#true_type). Gdy predykat typu ma *wartość false*, jest publicznie pochodny, bezpośrednio lub pośrednio, z [false_type](../standard-library/type-traits-typedefs.md#false_type).

*Modyfikator typu* lub *cecha przekształcenia* to szablon, który przyjmuje jeden lub więcej argumentów szablonu i ma jeden element członkowski, `type` który jest synonimem dla zmodyfikowanego typu.

### <a name="alias-templates"></a>Szablony aliasów

Aby uprościć wyrażenia cech typu, są udostępniane [Szablony aliasów](../cpp/aliases-and-typedefs-cpp.md) `typename some_trait<T>::type` , gdzie *some_trait* jest nazwą szablonu klasy. Na przykład [add_const](../standard-library/add-const-class.md) ma szablon aliasu dla typu, `add_const_t` , zdefiniowany jako:

```cpp
template <class T>
using add_const_t = typename add_const<T>::type;
```

Są to podane aliasy dla `type` członków:

:::row:::
   :::column:::
      `add_const_t`\
      `add_cv_t`\
      `add_lvalue_reference_t`\
      `add_pointer_t`\
      `add_rvalue_reference_t`\
      `add_volatile_t`\
      `aligned_storage_t`\
      `aligned_union_t`\
   :::column-end:::
   :::column:::
      `common_type_t`\
      `conditional_t`\
      `decay_t`\
      `enable_if_t`\
      `invoke_result_t`\
      `make_signed_t`\
      `make_unsigned_t`\
      `remove_all_extents_t`\
   :::column-end:::
   :::column:::
      `remove_const_t`\
      `remove_cv_t`\
      `remove_extent_t`\
      `remove_pointer_t`\
      `remove_reference_t`\
      `remove_volatile_t`\
      `result_of_t`\
      `underlying_type_t`\
   :::column-end:::
:::row-end:::

### <a name="classes"></a>Klasy

Klasa pomocnika i definicje typów

|Nazwa|Opis|
|-|-|
|[integral_constant](../standard-library/integral-constant-class-bool-constant-class.md)|Tworzy stałą całkowitą z typu i wartości.|
|[true_type](../standard-library/type-traits-typedefs.md#true_type)|Zawiera stałą całkowitą o wartości true.|
|[false_type](../standard-library/type-traits-typedefs.md#false_type)|Przechowuje stałą całkowitą z wartością false.|

Kategorie typów podstawowych

|Nazwa|Opis|
|-|-|
|[is_void](../standard-library/is-void-class.md)|Testuje, czy typ to **`void`** .|
|[is_null_pointer](../standard-library/is-null-pointer-class.md)|Testuje, czy typ to `std::nullptr_t` .|
|[is_integral](../standard-library/is-integral-class.md)|Testuje, czy typ jest całkowity.|
|[is_floating_point](../standard-library/is-floating-point-class.md)|Testuje, czy typ jest zmiennoprzecinkowy.|
|[is_array](../standard-library/is-array-class.md)|Testuje, czy typ jest tablicą.|
|[is_pointer](../standard-library/is-pointer-class.md)|Testuje, czy typ jest wskaźnikiem.|
|[is_lvalue_reference](../standard-library/is-lvalue-reference-class.md)|Testuje, czy typ jest odwołaniem lvalue.|
|[is_rvalue_reference](../standard-library/is-rvalue-reference-class.md)|Testuje, czy typ jest odwołaniem rvalue.|
|[is_member_object_pointer](../standard-library/is-member-object-pointer-class.md)|Testuje, czy typ jest wskaźnikiem do obiektu elementu członkowskiego.|
|[is_member_function_pointer](../standard-library/is-member-function-pointer-class.md)|Testuje, czy typ jest wskaźnikiem do funkcji składowej.|
|[is_enum](../standard-library/is-enum-class.md)|Testuje, czy typ jest wyliczeniem.|
|[is_union](../standard-library/is-union-class.md)|Testuje, czy typ jest Unią.|
|[is_class](../standard-library/is-class-class.md)|Testuje, czy typ jest klasą.|
|[is_function](../standard-library/is-function-class.md)|Testuje, czy typ jest typem funkcji.|

Kategorie typów złożonych

|Nazwa|Opis|
|-|-|
|[is_reference](../standard-library/is-reference-class.md)|Testuje, czy typ jest odwołaniem.|
|[is_arithmetic](../standard-library/is-arithmetic-class.md)|Testuje, czy typ jest arytmetyczny.|
|[is_fundamental](../standard-library/is-fundamental-class.md)|Testuje, czy typ jest **`void`** lub arytmetyczny.|
|[is_object](../standard-library/is-object-class.md)|Testuje, czy typ jest typem obiektu.|
|[is_scalar](../standard-library/is-scalar-class.md)|Testuje, czy typ jest skalarny.|
|[is_compound](../standard-library/is-compound-class.md)|Testuje, czy typ nie jest skalarny.|
|[is_member_pointer](../standard-library/is-member-pointer-class.md)|Testuje, czy typ jest wskaźnikiem do elementu członkowskiego.|

Właściwości typu

|Nazwa|Opis|
|-|-|
|[is_const](../standard-library/is-const-class.md)|Testuje, czy typ to **`const`** .|
|[is_volatile](../standard-library/is-volatile-class.md)|Testuje, czy typ to **`volatile`** .|
|[is_trivial](../standard-library/is-trivial-class.md)|Testuje, czy typ jest prosty.|
|[is_trivially_copyable](../standard-library/is-trivially-copyable-class.md)|Testuje, czy typ jest z możliwością kopiowania.|
|[is_standard_layout](../standard-library/is-standard-layout-class.md)|Testuje, czy typ jest standardowym typem układu.|
|[is_pod](../standard-library/is-pod-class.md)|Testuje, czy typ jest POD.|
|[is_literal_type](../standard-library/is-literal-type-class.md)|Testuje, czy typ może być **`constexpr`** zmienną lub używaną w **`constexpr`** funkcji.|
|[is_empty](../standard-library/is-empty-class.md)|Testuje, czy typ jest pustą klasą.|
|[is_polymorphic](../standard-library/is-polymorphic-class.md)|Testuje, czy typ jest klasą polimorficzną.|
|[is_abstract](../standard-library/is-abstract-class.md)|Testuje, czy typ jest klasą abstrakcyjną.|
|[is_final](../standard-library/is-final-class.md)|Testuje, czy typ jest oznaczony typem klasy `final` .|
|[is_aggregate](../standard-library/is-aggregate-class.md)||
|[is_signed](../standard-library/is-signed-class.md)|Testuje, czy typ jest cyfrową liczbą całkowitą.|
|[is_unsigned](../standard-library/is-unsigned-class.md)|Testuje, czy typ jest liczbą całkowitą bez znaku.|
|[is_constructible](../standard-library/is-constructible-class.md)|Testuje, czy typ jest konstrukcyjną przy użyciu określonych typów argumentów.|
|[is_default_constructible](../standard-library/type-traits-functions.md#is_default_constructible)|Testuje, czy typ ma konstruktora domyślnego.|
|[is_copy_constructible](../standard-library/type-traits-functions.md#is_copy_constructible)|Testuje, czy typ ma Konstruktor kopiujący.|
|[is_move_constructible](../standard-library/type-traits-functions.md#is_move_constructible)|Testuje, czy typ ma Konstruktor przenoszenia.|
|[is_assignable](../standard-library/type-traits-functions.md#is_assignable)|Testuje, czy do pierwszego typu można przypisać wartość drugiego typu.|
|[is_copy_assignable](../standard-library/type-traits-functions.md#is_copy_assignable)|Testuje, czy do typu może być przypisana stała wartość referencyjna typu.|
|[is_move_assignable](../standard-library/type-traits-functions.md#is_move_assignable)|Testuje, czy do typu można przypisać odwołanie rvalue typu.|
|[is_swappable](../standard-library/type-traits-functions.md#is_swappable)||
|[is_swappable_with](../standard-library/type-traits-functions.md#is_swappable_with)||
|[is_destructible](../standard-library/is-destructible-class.md)|Testuje, czy typem jest zniszczalnych.|
|[is_trivially_constructible](../standard-library/is-trivially-constructible-class.md)|Testuje, czy typ nie używa operacji nieuproszczonych podczas konstruowania przy użyciu określonych typów.|
|[is_trivially_default_constructible](../standard-library/is-trivially-default-constructible-class.md)|Testuje, czy typ nie używa operacji nieuproszczonych podczas konstruowania domyślnego.|
|[is_trivially_copy_constructible](../standard-library/is-trivially-copy-constructible-class.md)|Testuje, czy typ nie używa operacji nieuproszczonych podczas kopiowania.|
|[is_trivially_move_constructible](../standard-library/type-traits-functions.md#is_trivially_move_constructible)|Testuje, czy typ nie używa operacji nieuproszczonych podczas przenoszenia.|
|[is_trivially_assignable](../standard-library/is-trivially-assignable-class.md)|Testuje, czy typy są przypisane, a przypisanie nie używa operacji nieuproszczonych.|
|[is_trivially_copy_assignable](../standard-library/type-traits-functions.md#is_trivially_copy_assignable)|Testuje, czy typ jest możliwy do przydzielenia, a przypisanie nie używa operacji innych niż uproszczone.|
|[is_trivially_move_assignable](../standard-library/type-traits-functions.md#is_trivially_move_assignable)|Testuje, czy typ jest możliwy do przypisania, a przypisanie nie używa operacji innych niż uproszczone.|
|[is_trivially_destructible](../standard-library/is-trivially-destructible-class.md)|Testuje, czy typ to zniszczalnych, a destruktor nie używa operacji innych niż uproszczone.|
|[is_nothrow_constructible](../standard-library/is-nothrow-constructible-class.md)|Testuje, czy typ jest konstrukcyjną i nie jest zgłaszany, gdy jest konstruowany przy użyciu określonych typów.|
|[is_nothrow_default_constructible](../standard-library/is-nothrow-default-constructible-class.md)|Testuje, czy typ jest domyślny konstrukcyjną i nie jest zgłaszany podczas konstruowania domyślnego.|
|[is_nothrow_copy_constructible](../standard-library/is-nothrow-copy-constructible-class.md)|Testuje, czy typem jest Copy konstrukcyjną, i Konstruktor kopiujący jest nieznany, aby zgłosić.|
|[is_nothrow_move_constructible](../standard-library/is-nothrow-move-constructible-class.md)|Testuje, czy typ to Move konstrukcyjną, a Konstruktor przenoszenia jest nieznany, aby zgłosić.|
|[is_nothrow_assignable](../standard-library/is-nothrow-assignable-class.md)|Testuje, czy typ jest możliwy do przypisania przy użyciu określonego typu, a przypisanie jest znane, aby nie zgłosić.|
|[is_nothrow_copy_assignable](../standard-library/is-nothrow-copy-assignable-class.md)|Testuje, czy typ jest możliwy do przydzielenia, a przypisanie jest nieznane.|
|[is_nothrow_move_assignable](../standard-library/type-traits-functions.md#is_nothrow_move_assignable)|Testuje, czy typ jest przypisywany do przenoszenia i czy przypisanie jest znane, aby nie zgłosić.|
|[is_nothrow_swappable](../standard-library/type-traits-functions.md#is_nothrow_swappable)||
|[is_nothrow_swappable_with](../standard-library/type-traits-functions.md#is_nothrow_swappable_with)||
|[is_nothrow_destructible](../standard-library/is-nothrow-destructible-class.md)|Testuje, czy typem jest zniszczalnych i destruktorem nie należy zgłaszać.|
|`has_virtual_destructor`|Testuje, czy typ ma destruktor wirtualny.|
|`has_unique_object_representations`||
| [is_invocable](is-invocable-classes.md) | Testuje, czy możliwy do wywołania typ może być wywoływany przy użyciu określonych typów argumentów.<br/> Dodano w języku C++ 17. |
| [is_invocable_r](is-invocable-classes.md) | Testuje, czy możliwy do wywołania typ może być wywoływany przy użyciu określonych typów argumentów, a wynik jest konwertowany na określony typ.<br/> Dodano w języku C++ 17. |
| [is_nothrow_invocable](is-invocable-classes.md) | Testuje, czy możliwy do wywołania typ można wywołać przy użyciu określonych typów argumentów i czy nie należy zgłaszać wyjątków.<br/> Dodano w języku C++ 17. |
| [is_nothrow_invocable_r](is-invocable-classes.md) | Testuje, czy możliwy do wywołania typ może być wywoływany przy użyciu określonych typów argumentów i czy nie należy zgłaszać wyjątków, a wynik jest konwertowany na określony typ.<br/> Dodano w języku C++ 17. |

Zapytania właściwości typu

|Nazwa|Opis|
|-|-|
|[alignment_of](../standard-library/alignment-of-class.md)|Pobiera wyrównanie typu.|
|[stopni](../standard-library/rank-class.md)|Pobiera liczbę wymiarów tablicy.|
|[rozmiaru](../standard-library/extent-class.md)|Pobiera liczbę elementów w określonym wymiarze tablicy.|

Relacje typu

|Nazwa|Opis|
|-|-|
|[is_same](../standard-library/is-same-class.md)|Testuje, czy dwa typy są takie same.|
|[is_base_of](../standard-library/is-base-of-class.md)|Testuje, czy jeden typ jest podstawą innego.|
|[is_convertible](../standard-library/is-convertible-class.md)|Testuje, czy jeden typ jest konwertowany na inny.|

Nietrwałe modyfikacje

|Nazwa|Opis|
|-|-|
|[add_const](../standard-library/add-const-class.md)|Tworzy **`const`** Typ z typu.|
|[add_volatile](../standard-library/add-volatile-class.md)|Tworzy **`volatile`** Typ z typu.|
|[add_cv](../standard-library/add-cv-class.md)|Tworzy **`const volatile`** Typ z typu.|
|[remove_const](../standard-library/remove-const-class.md)|Tworzy typ inny niż const z typu.|
|[remove_volatile](../standard-library/remove-volatile-class.md)|Tworzy typ nietrwały od typu.|
|[remove_cv](../standard-library/remove-cv-class.md)|Tworzy typ inny niż const nietrwały od typu.|

Modyfikacje odwołań

|Nazwa|Opis|
|-|-|
|[add_lvalue_reference](../standard-library/add-lvalue-reference-class.md)|Tworzy odwołanie do typu z typu.|
|[add_rvalue_reference](../standard-library/add-rvalue-reference-class.md)|Tworzy odwołanie rvalue do typu z typu|
|[remove_reference](../standard-library/remove-reference-class.md)|Tworzy typ, który nie jest typem referencyjnym z typu.|

Modyfikacje podpisywania

|Nazwa|Opis|
|-|-|
|[make_signed](../standard-library/make-signed-class.md)|Tworzy typ, jeśli jest podpisany, lub najmniejszy typ ze znakiem większym niż lub równy rozmiarowi do typu.|
|[make_unsigned](../standard-library/make-unsigned-class.md)|Tworzy typ, jeśli nie jest podpisany, lub najmniejszy typ bez znaku, który jest większy niż lub równy rozmiarowi do typu.|

Modyfikacje tablicy

|Nazwa|Opis|
|-|-|
|[remove_all_extents](../standard-library/remove-all-extents-class.md)|Tworzy typ niebędący tablicą z typu tablicy.|
|[remove_extent](../standard-library/remove-extent-class.md)|Tworzy typ elementu z typu tablicy.|

Modyfikacje wskaźnika

|Nazwa|Opis|
|-|-|
|[add_pointer](../standard-library/add-pointer-class.md)|Tworzy wskaźnik do typu z typu.|
|[remove_pointer](../standard-library/remove-pointer-class.md)|Tworzy typ ze wskaźnika do typu.|

Inne przekształcenia

|Nazwa|Opis|
|-|-|
|[aligned_storage](../standard-library/aligned-storage-class.md)|Przydziela niezainicjowaną pamięć dla typu wyrównanego.|
|[aligned_union](../standard-library/aligned-union-class.md)|Przydziela niezainicjowaną pamięć dla Unii wyrównanej z nieprostym konstruktorem lub destruktorem.|
|[common_type](../standard-library/common-type-class.md)|Tworzy wspólny typ wszystkich typów pakietów parametrów.|
|[warunk](../standard-library/conditional-class.md)|Jeśli warunek ma wartość true, tworzy pierwszy określony typ, w przeciwnym razie drugi określony typ.|
|[nikając](../standard-library/decay-class.md)|Tworzy typ jako przekazaną przez wartość. Sprawia, że typ niebędący odwołaniem lub typem nietrwałym lub tworzy wskaźnik do typu.|
|[enable_if](../standard-library/enable-if-class.md)|Jeśli warunek ma wartość true, tworzy określony typ, w przeciwnym razie, bez typu.|
|[invoke_result](invoke-result-class.md)|Określa zwracany typ wywoływanego typu, który przyjmuje określone typy argumentów. <br/>Dodano w języku C++ 17. |
|[result_of](../standard-library/result-of-class.md)|Określa zwracany typ wywoływanego typu, który przyjmuje określone typy argumentów. <br/>Dodano w języku C++ 14, przestarzałe w języku C++ 17. |
|[underlying_type](../standard-library/underlying-type-class.md)|Tworzy podstawowy typ całkowity dla typu wyliczenia.|

Cechy operatora logicznego

|Nazwa|Opis|
|-|-|
|[działa](../standard-library/conjunction-class.md)||
|[rozłączenia](../standard-library/disjunction-class.md)||
|[negacji](../standard-library/negation-class.md)||

## <a name="see-also"></a>Zobacz też

[\<functional>](../standard-library/functional.md)
