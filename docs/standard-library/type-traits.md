---
title: '&lt;type_traits&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <type_traits>
dev_langs:
- C++
helpviewer_keywords:
- typetrait header
- type_traits
ms.assetid: 2260b51f-8160-4c66-a82f-00b534cb60d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5c7d09615b5f9ec7f0f72acde965d5ffbd018c9c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33863377"
---
# <a name="lttypetraitsgt"></a>&lt;type_traits&gt;

Definiuje szablony, które zapewniają stałe kompilacji, które zapewniają informacje o właściwościach ich argumentów typu lub utworzyć przekształcenia typów.

## <a name="syntax"></a>Składnia

```cpp
#include <type_traits>
```

## <a name="remarks"></a>Uwagi

Klasy i szablonów w \<type_traits > są używane do obsługi wnioskowanie o typie, klasyfikacji i przekształcenie w czasie kompilacji, do wykrywania błędów związanych z typem i można zoptymalizować kod rodzajowy. Te klasy i szablony obejmują jednoargumentowy cech typu w kompilatorze opisujących właściwości typu cech typu binarnego, które opisują relacji między typami i przekształcenie cech, które modyfikują właściwości typu.

Do obsługi cech typu, klasę pomocy `integral_constant`, jest zdefiniowany. Ma ona specjalizacji szablonu `true_type` i `false_type` który tworzą klas podstawowych dla typu predykatów. A *predykatu typów* to szablon, który przyjmuje jeden lub więcej argumentów typu. Jeśli predykat typów *jest spełniony*, jest publicznie pochodną, bezpośrednio lub pośrednio, z [true_type](../standard-library/type-traits-typedefs.md#true_type). Jeśli predykat typów *przechowuje false*, jest publicznie pochodną, bezpośrednio lub pośrednio, z [false_type](../standard-library/type-traits-typedefs.md#false_type).

A *modyfikator typu* lub *cechy przekształcania* szablon, który przyjmuje jeden lub więcej argumentów szablonu i ma jeden element członkowski, `type`, czyli synonimem typu zmodyfikowane.

### <a name="alias-templates"></a>Szablonów aliasów

Aby uprościć typu wyrażenia cech, [szablonów aliasów](../cpp/aliases-and-typedefs-cpp.md) dla `typename some_trait<T>::type` są dostarczane, gdzie " `some_trait`" jest nazwą klasy szablonu. Na przykład [add_const —](../standard-library/add-const-class.md) ma szablonu aliasu dla jego typu `add_const_t`, zdefiniowanej jako:

```cpp
template <class T>
using add_const_t = typename add_const<T>::type;
```

|||||
|-|-|-|-|
|add_const_t|aligned_storage_t|make_signed_t|remove_pointer_t|
|add_cv_t|aligned_union_t|make_unsigned_t|remove_reference_t|
|add_lvalue_reference_t|common_type_t|remove_all_extents_t|remove_volatile_t|
|add_pointer_t|conditional_t|remove_const_t|result_of_t|
|add_rvalue_reference_t|decay_t|remove_cv_t|underlying_type_t|
|add_volatile_t|enable_if_t|remove_extent_t||

### <a name="classes"></a>Klasy

Klasa pomocy i definicje typów

|||
|-|-|
|[integral_constant](../standard-library/integral-constant-class-bool-constant-class.md)|Sprawia, że typem całkowitym stałej od typu i wartości.|
|[true_type](../standard-library/type-traits-typedefs.md#true_type)|Przechowuje stałej o wartości true.|
|[false_type](../standard-library/type-traits-typedefs.md#false_type)|Przechowuje stałej o wartości false.|

Kategorie typu podstawowego

|||
|-|-|
|[is_void —](../standard-library/is-void-class.md)|Sprawdza, czy typ jest `void`.|
|[is_null_pointer](../standard-library/is-null-pointer-class.md)|Sprawdza, czy typ jest `std::nullptr_t`.|
|[is_integral](../standard-library/is-integral-class.md)|Sprawdza, czy typ jest integralną częścią.|
|[is_floating_point](../standard-library/is-floating-point-class.md)|Sprawdza, czy typ jest zmiennoprzecinkowych.|
|[is_array](../standard-library/is-array-class.md)|Sprawdza, czy typ jest tablicą.|
|[is_pointer](../standard-library/is-pointer-class.md)|Sprawdza, czy typ jest wskaźnik.|
|[is_lvalue_reference](../standard-library/is-lvalue-reference-class.md)|Testy, jeśli typ odwołania do wartości.|
|[is_rvalue_reference](../standard-library/is-rvalue-reference-class.md)|Testy, jeśli typ jest odwołanie do r-wartości.|
|[is_member_object_pointer](../standard-library/is-member-object-pointer-class.md)|Sprawdza, czy typ jest wskaźnik do obiektu elementu członkowskiego.|
|[is_member_function_pointer](../standard-library/is-member-function-pointer-class.md)|Sprawdza, czy typ jest wskaźnikiem do funkcji członkowskiej.|
|[is_enum](../standard-library/is-enum-class.md)|Sprawdza, czy typ jest wyliczeniem.|
|[is_union](../standard-library/is-union-class.md)|Sprawdza, czy typ jest Unii.|
|[is_class](../standard-library/is-class-class.md)|Sprawdza, czy typ jest klasą.|
|[is_function](../standard-library/is-function-class.md)|Sprawdza, czy typ jest typem funkcji.|

Kategorie typu złożonego

|||
|-|-|
|[is_reference](../standard-library/is-reference-class.md)|Sprawdza, czy typ jest odwołanie.|
|[is_arithmetic](../standard-library/is-arithmetic-class.md)|Sprawdza, czy typ jest arytmetyczne.|
|[is_fundamental](../standard-library/is-fundamental-class.md)|Sprawdza, czy typ jest `void` lub arytmetyczne.|
|[is_object](../standard-library/is-object-class.md)|Sprawdza, czy typ jest typem obiektu.|
|[is_scalar](../standard-library/is-scalar-class.md)|Sprawdza, czy typ jest skalarny.|
|[is_compound —](../standard-library/is-compound-class.md)|Sprawdza, czy typ nie jest skalarny.|
|[is_member_pointer](../standard-library/is-member-pointer-class.md)|Sprawdza, czy typ jest wskaźnik do elementu członkowskiego.|

Właściwości typu

|||
|-|-|
|[is_const](../standard-library/is-const-class.md)|Sprawdza, czy typ jest `const`.|
|[is_volatile](../standard-library/is-volatile-class.md)|Sprawdza, czy typ jest `volatile`.|
|[is_trivial](../standard-library/is-trivial-class.md)|Sprawdza, czy typ jest prosta.|
|[is_trivially_copyable](../standard-library/is-trivially-copyable-class.md)|Sprawdza, czy typ jest trivially copyable.|
|[is_standard_layout —](../standard-library/is-standard-layout-class.md)|Testy, jeśli typ jest typem standardowego układu.|
|[is_pod](../standard-library/is-pod-class.md)|Sprawdza, czy typ jest POD.|
|[is_literal_type](../standard-library/is-literal-type-class.md)|Sprawdza, czy typ może być `constexpr` zmiennej lub używanych w `constexpr` funkcji.|
|[is_empty](../standard-library/is-empty-class.md)|Sprawdza, czy typ jest pustą klasę.|
|[is_polymorphic](../standard-library/is-polymorphic-class.md)|Sprawdza, czy typ jest klasy polimorficznej.|
|[is_abstract](../standard-library/is-abstract-class.md)|Sprawdza, czy typ jest klasą abstrakcyjną.|
|[is_final](../standard-library/is-final-class.md)|Sprawdza, czy typ jest oznaczony jako typ klasy `final`.|
|[is_signed](../standard-library/is-signed-class.md)|Sprawdza, czy typ jest liczbę całkowitą ze znakiem.|
|[is_unsigned](../standard-library/is-unsigned-class.md)|Sprawdza, czy typ jest liczbą całkowitą bez znaku.|
|[is_constructible](../standard-library/is-constructible-class.md)|Sprawdza, czy typ jest umożliwia konstrukcji, przy użyciu określone typy argumentów.|
|[is_default_constructible](../standard-library/type-traits-functions.md#is_default_constructible)|Sprawdza, czy typ ma konstruktora domyślnego.|
|[is_copy_constructible](../standard-library/type-traits-functions.md#is_copy_constructible)|Sprawdza, czy typ ma konstruktora kopiującego.|
|[is_move_constructible](../standard-library/type-traits-functions.md#is_move_constructible)|Sprawdza, czy typ ma konstruktora przenoszenia.|
|[is_assignable](../standard-library/type-traits-functions.md#is_assignable)|Sprawdza, czy pierwszy typ można przypisać wartości typu drugiego.|
|[is_copy_assignable](../standard-library/type-traits-functions.md#is_copy_assignable)|Sprawdza, czy można przypisać typu stałej wartości odwołania typu.|
|[is_move_assignable](../standard-library/type-traits-functions.md#is_move_assignable)|Sprawdza, czy typ można przypisać odwołania do r-wartości typu.|
|[is_destructible](../standard-library/is-destructible-class.md)|Sprawdza, czy typ jest które można zniszczyć.|
|[is_trivially_constructible](../standard-library/is-trivially-constructible-class.md)|Sprawdza, czy typ korzysta z żadnych operacji nieuproszczony, gdy jest tworzony przy użyciu określonych typów.|
|[is_trivially_default_constructible](../standard-library/is-trivially-default-constructible-class.md)|Sprawdza, czy typ używa ma nieuproszczone operacji, gdy utworzony domyślny.|
|[is_trivially_copy_constructible](../standard-library/is-trivially-copy-constructible-class.md)|Sprawdza, czy typ używa ma nieuproszczone operacji podczas kopiowania skonstruowany.|
|[is_trivially_move_constructible](../standard-library/type-traits-functions.md#is_trivially_move_constructible)|Sprawdza, czy typ używa ma nieuproszczone operacji podczas przenoszenia skonstruowany.|
|[is_trivially_assignable](../standard-library/is-trivially-assignable-class.md)|Sprawdza, czy typy są można przypisać i nie ma operacji nieuproszczony korzysta z przypisania.|
|[is_trivially_copy_assignable](../standard-library/type-traits-functions.md#is_trivially_copy_assignable)|Określa, czy typ jest kopii można przypisać oraz przypisanie korzysta z żadnych operacji nieuproszczony testy.|
|[is_trivially_move_assignable](../standard-library/type-traits-functions.md#is_trivially_move_assignable)|Testy, czy typ jest możliwy do przypisania przenoszenia i przypisanie używa ma nieuproszczone operacji.|
|[is_trivially_destructible](../standard-library/is-trivially-destructible-class.md)|Sprawdza, czy typ które można zniszczyć, a destruktor używa ma nieuproszczone operacji.|
|[is_nothrow_constructible](../standard-library/is-nothrow-constructible-class.md)|Sprawdza, czy typ umożliwia konstrukcji, nie wiadomo throw, gdy jest tworzony przy użyciu określonych typów.|
|[is_nothrow_default_constructible](../standard-library/is-nothrow-default-constructible-class.md)|Testy typ domyślny umożliwia konstrukcji, nie wiadomo throw, gdy utworzony domyślny.|
|[is_nothrow_copy_constructible](../standard-library/is-nothrow-copy-constructible-class.md)|Sprawdza, czy typ jest kopią umożliwia konstrukcji, Konstruktor kopiujący wiadomo, że nie można zgłosić.|
|[is_nothrow_move_constructible](../standard-library/is-nothrow-move-constructible-class.md)|Sprawdza, czy typ jest przeniesienie umożliwia konstrukcji, Konstruktor przenoszenia wiadomo, że nie można zgłosić.|
|[is_nothrow_assignable](../standard-library/is-nothrow-assignable-class.md)|Sprawdza, czy typ jest możliwy do przypisania przy użyciu określonego typu i przypisanie wiadomo, że nie throw.|
|[is_nothrow_copy_assignable](../standard-library/is-nothrow-copy-assignable-class.md)|Sprawdza, czy typ jest możliwy do przypisania kopiowania i przypisanie wiadomo, że nie throw.|
|[is_nothrow_move_assignable](../standard-library/type-traits-functions.md#is_nothrow_move_assignable)|Sprawdza, czy typ jest możliwy do przypisania przenoszenia i przypisanie wiadomo, że nie throw.|
|[is_nothrow_destructible](../standard-library/is-nothrow-destructible-class.md)|Sprawdza, czy typ jest które można zniszczyć, destruktor wiadomo, że nie można zgłosić.|
|[has_virtual_destructor](http://msdn.microsoft.com/en-us/c0f85f0b-c63c-410d-a046-72eeaf44f7eb)|Sprawdza, czy typ ma destruktor wirtualny.|

Zapytania dotyczące właściwości typu

|||
|-|-|
|[alignment_of](../standard-library/alignment-of-class.md)|Pobiera wyrównanie typu.|
|[Ranga](../standard-library/rank-class.md)|Pobiera liczbę wymiarów tablicy.|
|[extent](../standard-library/extent-class.md)|Pobiera liczbę elementów w wymiarze określonej tablicy.|

Relacje typów

|||
|-|-|
|[is_same](../standard-library/is-same-class.md)|Sprawdza, czy dwa typy są takie same.|
|[is_base_of](../standard-library/is-base-of-class.md)|Sprawdza, czy jest jeden typ podstawowy innego.|
|[is_convertible](../standard-library/is-convertible-class.md)|Sprawdza, czy jest możliwe do przekonwertowania na inny.|

Modyfikacje Const-volatile

|||
|-|-|
|[add_const —](../standard-library/add-const-class.md)|Tworzy `const` typu z typu.|
|[add_volatile —](../standard-library/add-volatile-class.md)|Tworzy `volatile` typu z typu.|
|[add_cv](../standard-library/add-cv-class.md)|Tworzy `const volatile` typu z typu.|
|[remove_const](../standard-library/remove-const-class.md)|Tworzy z systemem innym niż stała typu z typu.|
|[remove_volatile](../standard-library/remove-volatile-class.md)|Tworzy trwałą typu z typu.|
|[remove_cv](../standard-library/remove-cv-class.md)|Tworzy typ trwałej z systemem innym niż stała typu.|

Modyfikacje odwołania

|||
|-|-|
|[add_lvalue_reference](../standard-library/add-lvalue-reference-class.md)|Tworzy odwołanie do typu z typu.|
|[add_rvalue_reference](../standard-library/add-rvalue-reference-class.md)|Tworzy odwołania do r-wartości do typu z typu|
|[remove_reference —](../standard-library/remove-reference-class.md)|Tworzy typ innych niż odwołania z typu.|

Modyfikacje logowania

|||
|-|-|
|[make_signed](../standard-library/make-signed-class.md)|Tworzy typ, jeśli podpisany lub najmniejszą podpisem typu mniejsza niż rozmiar typu.|
|[make_unsigned](../standard-library/make-unsigned-class.md)|Tworzy typ, jeśli bez znaku lub najmniejszą typu bez znaku mniejsza niż rozmiar typu.|

Modyfikacje tablicy

|||
|-|-|
|[remove_all_extents —](../standard-library/remove-all-extents-class.md)|Tworzy typu nietablicowego z typem tablicy.|
|[remove_extent](../standard-library/remove-extent-class.md)|Tworzy typ elementu z typem tablicy.|

Modyfikacje wskaźnika

|||
|-|-|
|[add_pointer](../standard-library/add-pointer-class.md)|Tworzy wskaźnika do typu z typu.|
|[remove_pointer](../standard-library/remove-pointer-class.md)|Tworzy typ ze wskaźnika do typu.|

Inne przekształcenia

|||
|-|-|
|[aligned_storage](../standard-library/aligned-storage-class.md)|Przydziela niezainicjowanej pamięci dla typu wyrównane.|
|[aligned_union](../standard-library/aligned-union-class.md)|Przydziela niezainicjowanej pamięci dla Unii wyrównany z nieuproszczony konstruktora lub destruktora.|
|[common_type](../standard-library/common-type-class.md)|Tworzy spotykane typy pakiet parametrów.|
|[warunkowe](../standard-library/conditional-class.md)|Jeśli warunek jest spełniony, tworzy pierwszy określonego typu, w przeciwnym razie drugi określonego typu.|
|[decay](../standard-library/decay-class.md)|Tworzy typ jako przekazany przez wartość. Sprawia, że typ bez odwołań, wartością stałą lub trwałej lub sprawia, że wskaźnik do typu.|
|[enable_if](../standard-library/enable-if-class.md)|Jeśli warunek jest spełniony, tworzy określonego typu, w przeciwnym razie bez typu.|
|[result_of](../standard-library/result-of-class.md)|Określa typ zwracany można wywołać typu, który pobiera określone typy argumentów.|
|[underlying_type](../standard-library/underlying-type-class.md)|Tworzy integralną typ podstawowy dla typu wyliczenia.|

## <a name="see-also"></a>Zobacz także

[\<functional>](../standard-library/functional.md)<br/>
