---
title: '&lt;type_traits&gt;'
ms.date: 02/21/2019
f1_keywords:
- <type_traits>
helpviewer_keywords:
- typetrait header
- type_traits
ms.assetid: 2260b51f-8160-4c66-a82f-00b534cb60d4
ms.openlocfilehash: c80629fd8771206d193b53aa7c32073de0ba45dd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62278985"
---
# <a name="lttypetraitsgt"></a>&lt;type_traits&gt;

Definiuje szablonów dla stałych kompilacji, które podają informacje o właściwościach ich argumentów typu lub wygenerować typy przekształcone.

## <a name="syntax"></a>Składnia

```cpp
#include <type_traits>
```

## <a name="remarks"></a>Uwagi

Klasy i szablonów w \<type_traits > są używane do obsługi wnioskowanie o typie, klasyfikacji i transformacji, w czasie kompilacji. Są również używane do wykrywania błędów dotyczących typu i ułatwiające optymalizację kodu ogólnego. Cech typu jednoelementowego opisywania właściwości typu, cech typu binary opisywania relacji między tymi typami i cechy przekształcania modyfikowania właściwości typu.

Klasa Pomocnika `integral_constant` i jego specjalizacji szablonu `true_type` i `false_type` tworzą klas bazowych dla typu predykatów. A *predykatu typów* jest szablon, który przyjmuje jeden lub więcej argumentów typu. Jeśli predykat typów *prawdziwe*, publicznie pochodzi, bezpośrednio lub pośrednio z [true_type](../standard-library/type-traits-typedefs.md#true_type). Jeśli predykat typów *przechowuje wartość false*, publicznie pochodzi, bezpośrednio lub pośrednio z [false_type](../standard-library/type-traits-typedefs.md#false_type).

A *modyfikatora typu* lub *cech przekształcania* jest szablon, który przyjmuje jeden lub więcej argumentów szablonu, a ma jeden element członkowski, `type`, co jest synonimem typu zmodyfikowane.

### <a name="alias-templates"></a>Szablony aliasów

Aby uprościć typ cechy wyrażeń, [szablony aliasów](../cpp/aliases-and-typedefs-cpp.md) dla `typename some_trait<T>::type` są dostarczane, gdy *some_trait* jest nazwą klasy szablonu. Na przykład [add_const —](../standard-library/add-const-class.md) ma szablonie aliasu dla tego typu `add_const_t`, zdefiniowany jako:

```cpp
template <class T>
using add_const_t = typename add_const<T>::type;
```

Oto aliasy podana dla `type` elementy członkowskie:

||||
|-|-|-|
| add_const_t | add_cv_t | add_lvalue_reference_t |
| add_pointer_t | add_rvalue_reference_t | add_volatile_t |
| aligned_storage_t | aligned_union_t | common_type_t |
| conditional_t | decay_t | enable_if_t |
| invoke_result_t | make_signed_t | make_unsigned_t |
| remove_all_extents_t | remove_const_t | remove_cv_t |
| remove_extent_t | remove_pointer_t | remove_reference_t |
| remove_volatile_t | result_of_t | underlying_type_t |

### <a name="classes"></a>Klasy

Klasa pomocnika i definicje typów

|||
|-|-|
|[integral_constant](../standard-library/integral-constant-class-bool-constant-class.md)|Sprawia, że całkowita stałe od typu i wartości.|
|[true_type](../standard-library/type-traits-typedefs.md#true_type)|Zawiera stałą całkowitą o wartości true.|
|[false_type](../standard-library/type-traits-typedefs.md#false_type)|Zawiera stałą całkowitą o wartości false.|

Kategorie typu podstawowego

|||
|-|-|
|[is_void](../standard-library/is-void-class.md)|Sprawdza, czy typ jest **void**.|
|[is_null_pointer](../standard-library/is-null-pointer-class.md)|Sprawdza, czy typ jest `std::nullptr_t`.|
|[is_integral](../standard-library/is-integral-class.md)|Sprawdza, czy typ jest integralną częścią.|
|[is_floating_point](../standard-library/is-floating-point-class.md)|Sprawdza, czy typ jest zmiennoprzecinkowych.|
|[is_array](../standard-library/is-array-class.md)|Sprawdza, czy typ jest tablicą.|
|[is_pointer](../standard-library/is-pointer-class.md)|Sprawdza, czy typ jest wskaźnikiem.|
|[is_lvalue_reference](../standard-library/is-lvalue-reference-class.md)|Sprawdza, czy typ jest odwołaniem lvalue.|
|[is_rvalue_reference](../standard-library/is-rvalue-reference-class.md)|Sprawdza, czy typ jest odwołaniem rvalue.|
|[is_member_object_pointer](../standard-library/is-member-object-pointer-class.md)|Sprawdza, czy typ jest wskaźnik do obiektu elementu członkowskiego.|
|[is_member_function_pointer](../standard-library/is-member-function-pointer-class.md)|Sprawdza, czy typ jest wskaźnikiem do funkcji członkowskiej.|
|[is_enum](../standard-library/is-enum-class.md)|Sprawdza, czy typ jest wyliczeniem.|
|[is_union](../standard-library/is-union-class.md)|Sprawdza, czy typ jest Unii.|
|[is_class](../standard-library/is-class-class.md)|Sprawdza, czy typ jest klasą.|
|[is_function](../standard-library/is-function-class.md)|Sprawdza, czy typ jest typem funkcji.|

Typ złożony kategorii

|||
|-|-|
|[is_reference](../standard-library/is-reference-class.md)|Sprawdza, czy typ jest odwołaniem.|
|[is_arithmetic](../standard-library/is-arithmetic-class.md)|Sprawdza, czy typ jest arytmetyczne.|
|[is_fundamental](../standard-library/is-fundamental-class.md)|Sprawdza, czy typ jest **void** lub arytmetyczne.|
|[is_object](../standard-library/is-object-class.md)|Sprawdza, czy typ jest typem obiektu.|
|[is_scalar](../standard-library/is-scalar-class.md)|Sprawdza, czy typ jest skalarna.|
|[is_compound](../standard-library/is-compound-class.md)|Sprawdza, czy określony typ nie jest skalarny.|
|[is_member_pointer](../standard-library/is-member-pointer-class.md)|Sprawdza, czy typ jest wskaźnik do elementu członkowskiego.|

Właściwości typu

|||
|-|-|
|[is_const](../standard-library/is-const-class.md)|Sprawdza, czy typ jest **const**.|
|[is_volatile](../standard-library/is-volatile-class.md)|Sprawdza, czy typ jest **volatile**.|
|[is_trivial](../standard-library/is-trivial-class.md)|Sprawdza, czy typ jest proste.|
|[is_trivially_copyable](../standard-library/is-trivially-copyable-class.md)|Sprawdza, czy typ jest kopiowania.|
|[is_standard_layout](../standard-library/is-standard-layout-class.md)|Sprawdza, czy typ jest typem standardowego układu.|
|[is_pod](../standard-library/is-pod-class.md)|Sprawdza, czy typ jest ZASOBNIK.|
|[is_literal_type](../standard-library/is-literal-type-class.md)|Sprawdza, czy typ może być `constexpr` zmiennej lub używany w `constexpr` funkcji.|
|[is_empty](../standard-library/is-empty-class.md)|Sprawdza, czy typ jest pustą klasę.|
|[is_polymorphic](../standard-library/is-polymorphic-class.md)|Sprawdza, czy typ jest polimorficznej klasy.|
|[is_abstract](../standard-library/is-abstract-class.md)|Sprawdza, czy typ jest klasą abstrakcyjną.|
|[is_final](../standard-library/is-final-class.md)|Sprawdza, czy typ jest typem klasy oznaczone `final`.|
|[is_signed](../standard-library/is-signed-class.md)|Sprawdza, czy typ jest liczba całkowita ze znakiem.|
|[is_unsigned](../standard-library/is-unsigned-class.md)|Sprawdza, czy typ jest liczbą całkowitą bez znaku.|
|[is_constructible](../standard-library/is-constructible-class.md)|Sprawdza, czy typ jest konstrukcyjną, za pomocą określone typy argumentów.|
|[is_default_constructible](../standard-library/type-traits-functions.md#is_default_constructible)|Sprawdza, czy typ ma konstruktora domyślnego.|
|[is_copy_constructible](../standard-library/type-traits-functions.md#is_copy_constructible)|Sprawdza, czy typ ma konstruktora kopiującego.|
|[is_move_constructible](../standard-library/type-traits-functions.md#is_move_constructible)|Sprawdza, czy typ ma konstruktora przenoszącego.|
|[is_assignable](../standard-library/type-traits-functions.md#is_assignable)|Sprawdza, czy pierwszy typ można przypisać wartości drugiego typu.|
|[is_copy_assignable](../standard-library/type-traits-functions.md#is_copy_assignable)|Sprawdza, czy można przypisać typu const wartość odwołanie do typu.|
|[is_move_assignable](../standard-library/type-traits-functions.md#is_move_assignable)|Sprawdza, czy typ można przypisać typu odwołanie rvalue.|
|[is_destructible](../standard-library/is-destructible-class.md)|Sprawdza, czy typ jest zniszczalnych.|
|[is_trivially_constructible](../standard-library/is-trivially-constructible-class.md)|Sprawdza, czy typ korzysta z żadnych operacji nietrywialnymi, gdy tworzony przy użyciu określonego typu.|
|[is_trivially_default_constructible](../standard-library/is-trivially-default-constructible-class.md)|Sprawdza, czy typ używa ma nieuproszczone operacji, gdy domyślny skonstruowany.|
|[is_trivially_copy_constructible](../standard-library/is-trivially-copy-constructible-class.md)|Sprawdza, czy typ używa żadne operacje nietrywialnymi podczas kopiowania skonstruowany.|
|[is_trivially_move_constructible](../standard-library/type-traits-functions.md#is_trivially_move_constructible)|Sprawdza, czy typ używa ma nieuproszczone operacji, podczas przenoszenia skonstruowany.|
|[is_trivially_assignable](../standard-library/is-trivially-assignable-class.md)|Sprawdza, czy typy są możliwe do przypisania i przypisanie używa ma nieuproszczone operacji.|
|[is_trivially_copy_assignable](../standard-library/type-traits-functions.md#is_trivially_copy_assignable)|Sprawdza, czy typ jest możliwy do przypisania kopii oraz przypisanie korzysta z żadnych nietrywialnymi operacji.|
|[is_trivially_move_assignable](../standard-library/type-traits-functions.md#is_trivially_move_assignable)|Sprawdza, czy typ jest możliwy do przypisania przenoszenia oraz przypisanie korzysta z żadnych nietrywialnymi operacji.|
|[is_trivially_destructible](../standard-library/is-trivially-destructible-class.md)|Sprawdza, czy typ jest zniszczalnych i destruktor używa ma nieuproszczone operacji.|
|[is_nothrow_constructible](../standard-library/is-nothrow-constructible-class.md)|Sprawdza, czy typ jest konstrukcyjną, wiadomo, nie zgłaszają, gdy jest tworzona przy użyciu określonego typu.|
|[is_nothrow_default_constructible](../standard-library/is-nothrow-default-constructible-class.md)|Testy typ domyślny konstrukcyjną, wiadomo, nie zgłaszają, gdy domyślny skonstruowany.|
|[is_nothrow_copy_constructible](../standard-library/is-nothrow-copy-constructible-class.md)|Sprawdza, czy typ jest kopią konstrukcyjną, Konstruktor kopiujący wiadomo, że nie zostać zgłoszony.|
|[is_nothrow_move_constructible](../standard-library/is-nothrow-move-constructible-class.md)|Sprawdza, czy typ jest przeniesienie konstrukcyjną, Konstruktor przenoszący wiadomo, że nie zostać zgłoszony.|
|[is_nothrow_assignable](../standard-library/is-nothrow-assignable-class.md)|Sprawdza, czy typ jest możliwy do przypisania, przy użyciu określonego typu, przypisanie wiadomo, że nie zostać zgłoszony.|
|[is_nothrow_copy_assignable](../standard-library/is-nothrow-copy-assignable-class.md)|Sprawdza, czy typ jest możliwy do przypisania kopiowania, przypisanie wiadomo, że nie zostać zgłoszony.|
|[is_nothrow_move_assignable](../standard-library/type-traits-functions.md#is_nothrow_move_assignable)|Sprawdza, czy typ jest możliwy do przypisania przeniesienia, przypisanie wiadomo, że nie zostać zgłoszony.|
|[is_nothrow_destructible](../standard-library/is-nothrow-destructible-class.md)|Sprawdza, czy typ jest zniszczalnych, destruktor wiadomo, że nie zostać zgłoszony.|
|`has_virtual_destructor`|Sprawdza, czy typ ma destruktor wirtualny.|
| [is_invocable](is-invocable-classes.md) | Sprawdza, czy możliwy do wywołania typu może być wywoływany przy użyciu określone typy argumentów.<br/> Dodane w języku C ++ 17. |
| [is_invocable_r](is-invocable-classes.md) | Sprawdza, czy możliwy do wywołania typu może być wywoływany przy użyciu określone typy argumentów i wynik jest konwertowany na typ określony.<br/> Dodane w języku C ++ 17. |
| [is_nothrow_invocable](is-invocable-classes.md) | Sprawdza, czy możliwy do wywołania typu może być wywoływany przy użyciu określonego argumentu typów, wiadomo, nie zgłasza wyjątków.<br/> Dodane w języku C ++ 17. |
| [is_nothrow_invocable_r](is-invocable-classes.md) | Sprawdza, czy możliwy do wywołania typu może być wywoływany przy użyciu określone typy argumentów, wiadomo, nie generują wyjątki, a wynik jest konwertowany na określony typ.<br/> Dodane w języku C ++ 17. |

Zapytania dotyczące właściwości typu

|||
|-|-|
|[alignment_of](../standard-library/alignment-of-class.md)|Pobiera wyrównania tekstu.|
|[rank](../standard-library/rank-class.md)|Pobiera liczbę wymiarów tablicy.|
|[extent](../standard-library/extent-class.md)|Pobiera liczbę elementów w wymiarze określonej tablicy.|

Typ relacji

|||
|-|-|
|[is_same](../standard-library/is-same-class.md)|Sprawdza, czy dwa typy są takie same.|
|[is_base_of](../standard-library/is-base-of-class.md)|Sprawdza, czy jest jeden typ podstawowy innego.|
|[is_convertible](../standard-library/is-convertible-class.md)|Sprawdza, czy jeden typ jest konwertowany na inny.|

Modyfikacje Const-volatile

|||
|-|-|
|[add_const](../standard-library/add-const-class.md)|Tworzy **const** typu z typu.|
|[add_volatile](../standard-library/add-volatile-class.md)|Tworzy **volatile** typu z typu.|
|[add_cv](../standard-library/add-cv-class.md)|Tworzy **const volatile** typu z typu.|
|[remove_const](../standard-library/remove-const-class.md)|Tworzy typ niestały z typu.|
|[remove_volatile](../standard-library/remove-volatile-class.md)|Tworzy typ-volatile z typu.|
|[remove_cv](../standard-library/remove-cv-class.md)|Tworzy typ niestały volatile z typu.|

Odwołanie do modyfikacji

|||
|-|-|
|[add_lvalue_reference](../standard-library/add-lvalue-reference-class.md)|Tworzy odwołanie do typu z typu.|
|[add_rvalue_reference](../standard-library/add-rvalue-reference-class.md)|Tworzy odwołanie rvalue do typu z typu|
|[remove_reference](../standard-library/remove-reference-class.md)|Tworzy typ inny niż odwołanie z typu.|

Zmiany logowania

|||
|-|-|
|[make_signed](../standard-library/make-signed-class.md)|Tworzy typ, jeśli podpisany lub najmniejszy typ ze znakiem mniejszy niż rozmiar do typu.|
|[make_unsigned](../standard-library/make-unsigned-class.md)|Tworzy typ, jeśli bez znaku lub najmniejszego typu bez znaku mniejszy niż rozmiar, aby wpisać.|

Modyfikacje tablicy

|||
|-|-|
|[remove_all_extents](../standard-library/remove-all-extents-class.md)|Tworzy typ inny niż tablica z typu tablicy.|
|[remove_extent](../standard-library/remove-extent-class.md)|Tworzy typ elementu z typu tablicy.|

Wskaźnik zmiany

|||
|-|-|
|[add_pointer](../standard-library/add-pointer-class.md)|Tworzy wskaźnik do typu z typu.|
|[remove_pointer](../standard-library/remove-pointer-class.md)|Tworzy typ ze wskaźnika do typu.|

Inne przekształcenia

|||
|-|-|
|[aligned_storage](../standard-library/aligned-storage-class.md)|Przydziela wyrównany typ. niezainicjowanej pamięci.|
|[aligned_union](../standard-library/aligned-union-class.md)|Przydziela niezainicjowanej pamięci dla Unii wyrównany z nietrywialnymi Konstruktor lub destruktor.|
|[common_type](../standard-library/common-type-class.md)|Tworzy typ wspólny wszystkich typów pakiet parametrów.|
|[warunkowe](../standard-library/conditional-class.md)|Jeśli warunek jest spełniony, tworzy pierwszego określonego typu, w przeciwnym razie drugiego określonego typu.|
|[decay](../standard-library/decay-class.md)|Tworzy typ, jak przekazać przez wartość. Tworzy typ niebędący odniesieniem, niestały lub trwałej lub tworzy wskaźnik do typu.|
|[enable_if](../standard-library/enable-if-class.md)|Jeśli warunek jest spełniony, tworzy określonego typu, w przeciwnym razie bez typu.|
|[invoke_result](invoke-result-class.md)|Określa typ zwracany typ możliwy do wywołania, który przyjmuje określone typy argumentów. <br/>Dodane w języku C ++ 17. |
|[result_of](../standard-library/result-of-class.md)|Określa typ zwracany typ możliwy do wywołania, który przyjmuje określone typy argumentów. <br/>Dodane w języku C ++ 14, uznane za przestarzałe w języku C ++ 17. |
|[underlying_type](../standard-library/underlying-type-class.md)|Tworzy podstawowy typ całkowitą typ wyliczenia.|

## <a name="see-also"></a>Zobacz także

[\<functional>](../standard-library/functional.md)<br/>
