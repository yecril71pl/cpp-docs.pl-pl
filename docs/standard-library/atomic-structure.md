---
title: atomic — Struktura
ms.date: 04/20/2018
f1_keywords:
- atomic/std::atomic
ms.assetid: 261628ed-7049-41ac-99b9-cfe49f696b44
ms.openlocfilehash: 1b3b60d71fcdf68fdf215820535c3bfb3d4dfb2b
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456734"
---
# <a name="atomic-structure"></a>atomic — Struktura

Opisuje obiekt, który wykonuje operacje niepodzielne na wartości przechowywanej typu *ty*.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct atomic;
```

## <a name="members"></a>Elementy członkowskie

|Element członkowski|Opis|
|----------|-----------------|
|**Konstruktora**||
|[atomic](#atomic)|Konstruuje obiekt niepodzielny.|
|**Operatory**||
|[niepodzielna:: operator ty](#op_ty)|Odczytuje i zwraca przechowywaną wartość. ([niepodzielna:: Load](#load))|
|[niepodzielna:: operator =](#op_eq)|Używa określonej wartości w celu zastąpienia przechowywanej wartości. ([niepodzielna:: Store](#store))|
|[niepodzielna:: operator + +](#op_inc)|Zwiększa wartość przechowywaną. Używane tylko przez specjalizacje w postaci integralnej i wskaźnika.|
|[niepodzielna:: operator + =](#op_add_eq)|Dodaje określoną wartość do przechowywanej wartości. Używane tylko przez specjalizacje w postaci integralnej i wskaźnika.|
|[niepodzielna:: operator--](#op_dec)|Zmniejsza przechowywaną wartość. Używane tylko przez specjalizacje w postaci integralnej i wskaźnika.|
|[niepodzielna:: operator-=](#op_sub_eq)|Odejmuje określoną wartość z przechowywanej wartości. Używane tylko przez specjalizacje w postaci integralnej i wskaźnika.|
|[niepodzielna:: operator & =](#op_and_eq)|Wykonuje wartości bitowe i w określonej wartości oraz przechowywaną wartość. Używane tylko przez całkowitą specjalizację.|
|[niepodzielna:&#124;: operator =](#op_or_eq)|Wykonuje wartość bitową lub dla określonej wartości oraz wartości przechowywanej. Używane tylko przez całkowitą specjalizację.|
|[niepodzielna:: operator ^ =](#op_xor_eq)|Wykonuje bitowe wykluczające lub dla określonej wartości oraz wartości przechowywanej. Używane tylko przez całkowitą specjalizację.|
|**Funkcje**||
|[compare_exchange_strong](#compare_exchange_strong)|Wykonuje operację *atomic_compare_and_exchange* na **tym** i zwraca wynik.|
|[compare_exchange_weak](#compare_exchange_weak)|Wykonuje operację *weak_atomic_compare_and_exchange* na **tym** i zwraca wynik.|
|[fetch_add](#fetch_add)|Dodaje określoną wartość do przechowywanej wartości.|
|[fetch_and](#fetch_and)|Wykonuje wartości bitowe i w określonej wartości oraz przechowywaną wartość.|
|[fetch_or](#fetch_or)|Wykonuje wartość bitową lub dla określonej wartości oraz wartości przechowywanej.|
|[fetch_sub](#fetch_sub)|Odejmuje określoną wartość z przechowywanej wartości.|
|[fetch_xor](#fetch_xor)|Wykonuje bitowe wykluczające lub dla określonej wartości oraz wartości przechowywanej.|
|[is_lock_free](#is_lock_free)|Określa, czy operacje niepodzielne w **tej** usłudze są *wolne od blokady*. Typ niepodzielny jest *zablokowany* , jeśli żadna niepodzielna operacja nie używa blokad.|
|[ładowania](#load)|Odczytuje i zwraca przechowywaną wartość.|
|[zachować](#store)|Używa określonej wartości w celu zastąpienia przechowywanej wartości.|

## <a name="remarks"></a>Uwagi

Typ *ty* musi być jednocześnie *kopiowany*. Oznacza to, że użycie [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) do kopiowania jego bajtów musi generować prawidłowy obiekt *ty* , który porównuje równy pierwotnemu obiektowi. Funkcje członkowskie [compare_exchange_weak](#compare_exchange_weak) i [compare_exchange_strong](#compare_exchange_strong) używają [funkcji memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md) do określenia, *czy dwie wartości* są równe. Te funkcje nie będą używały zdefiniowanego `operator==`przez ty elementu. Funkcje `atomic` składowe używane `memcpy` do kopiowania wartości typu *ty*.

Częściowa specjalizacja, **niepodzielna\<br \* >** , istnieje dla wszystkich typów wskaźnika. Specjalizacja umożliwia dodanie przesunięcia do wartości wskaźnika zarządzanego lub odejmowania przesunięcia. Operacje arytmetyczne przyjmują argument typu `ptrdiff_t` i dostosowują ten argument zgodnie z rozmiarem *ty* , aby był spójny ze zwykłym arytmetycznym adresem.

Specjalizacja istnieje dla każdego typu całkowitego, z wyjątkiem **bool**. Każda specjalizacja oferuje bogaty zestaw metod operacji arytmetycznych i logicznych.

||||
|-|-|-|
|**>\<znaków niepodzielnych**|**niepodzielna\<cyfra > znaku**|**niepodzielny\<znak bez znaku >**|
|**niepodzielne\<> char16_t**|**niepodzielne\<> char32_t**|**niepodzielne\<> wchar_t**|
|**Krótka > niepodzielna\<**|**niepodzielna\<nieniepodpisana >**|**niepodzielna\<> int**|
|**niepodzielna\<niepodpisane > int**|**liczba\<niepodzielna >**|**niepodzielna\<cyfrowo niepodpisana >**|
|**niepodzielna\<> długa Long**|**niepodzielna\<cyfrowo niepodpisana >**|

Integralne specjalizacje są uzyskiwane `atomic_integral` z odpowiednich typów. Na przykład niepodzielne **\<niepodpisane > int** są `atomic_uint`wyprowadzane z.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> niepodzielne

**Przestrzeń nazw:** std

## <a name="atomic"></a>niepodzielna:: niepodzielna

Konstruuje obiekt niepodzielny.

```cpp
atomic();
atomic( const atomic& );
atomic( Ty Value ) noexcept;
```

### <a name="parameters"></a>Parametry

*Wartościami*\
Wartość inicjalizacji.

### <a name="remarks"></a>Uwagi

Nie można skopiować ani przenieść obiektów niepodzielnych.

Obiekty, które są wystąpieniami\<*niepodzielnych*, > mogą być inicjowane tylko przez konstruktora, który przyjmuje argument typu *ty* , a nie za pomocą inicjowania agregacji. Jednak obiekty atomic_integral mogą być inicjowane tylko przy użyciu inicjowania agregacji.

```cpp
atomic<int> ai0 = ATOMIC_VAR_INIT(0);
atomic<int> ai1(0);
```

## <a name="op_ty"></a>niepodzielna:: operator *ty*

Operator dla typu określonego dla szablonu,\<*niepodzielny*>. Pobiera wartość przechowywaną w  **\*tym**elemencie.

```cpp
atomic<Ty>::operator Ty() const volatile noexcept;
atomic<Ty>::operator Ty() const noexcept;
```

### <a name="remarks"></a>Uwagi

Ten operator stosuje `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_eq"></a>niepodzielna:: operator =

Przechowuje określoną wartość.

```cpp
Ty operator=(
   Ty Value
) volatile noexcept;
Ty operator=(
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Parametry

*Wartościami*\
Obiekt *ty* .

### <a name="return-value"></a>Wartość zwracana

Zwraca *wartość*.

## <a name="op_inc"></a>niepodzielna:: operator + +

Zwiększa wartość przechowywaną. Używane tylko przez specjalizacje w postaci integralnej i wskaźnika.

```cpp
Ty atomic<Ty>::operator++(int) volatile noexcept;
Ty atomic<Ty>::operator++(int) noexcept;
Ty atomic<Ty>::operator++() volatile noexcept;
Ty atomic<Ty>::operator++() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Pierwsze dwa operatory zwracają wartość przyrostową; ostatnie dwa operatory zwracają wartość przed przyrostem. Operatory używają `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_add_eq"></a>niepodzielna:: operator + =

Dodaje określoną wartość do przechowywanej wartości. Używane tylko przez specjalizacje w postaci integralnej i wskaźnika.

```cpp
Ty atomic<Ty>::operator+=(
   Ty Value
) volatile noexcept;
Ty atomic<Ty>::operator+=(
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Parametry

*Wartościami*\
Wartość całkowita lub wskaźnik.

### <a name="return-value"></a>Wartość zwracana

Obiekt *ty* , który zawiera wynik dodania.

### <a name="remarks"></a>Uwagi

Ten operator używa `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_dec"></a>niepodzielna:: operator--

Zmniejsza przechowywaną wartość. Używane tylko przez specjalizacje w postaci integralnej i wskaźnika.

```cpp
Ty atomic<Ty>::operator--(int) volatile noexcept;
Ty atomic<Ty>::operator--(int) noexcept;
Ty atomic<Ty>::operator--() volatile noexcept;
Ty atomic<Ty>::operator--() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Pierwsze dwa operatory zwracają wartość, która jest zmniejszana; ostatnie dwa operatory zwracają wartość przed zmniejszeniem. Operatory używają `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_sub_eq"></a>niepodzielna:: operator-=

Odejmuje określoną wartość z przechowywanej wartości. Używane tylko przez specjalizacje w postaci integralnej i wskaźnika.

```cpp
Ty atomic<Ty>::operator-=(
   Ty Value
) volatile noexcept;
Ty atomic<Ty>::operator-=(
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Parametry

*Wartościami*\
Wartość całkowita lub wskaźnik.

### <a name="return-value"></a>Wartość zwracana

Obiekt *ty* , który zawiera wynik odejmowania.

### <a name="remarks"></a>Uwagi

Ten operator używa `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_and_eq"></a>niepodzielna:: operator & =

Wykonuje wartości bitowe i w określonej wartości oraz przechowywaną  **\*wartość.** Używane tylko przez całkowitą specjalizację.

```cpp
atomic<Ty>::operator&= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator&= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Parametry

*Wartościami*\
Wartość typu *ty*.

### <a name="return-value"></a>Wartość zwracana

Wynik bitowy i.

### <a name="remarks"></a>Uwagi

Ten operator wykonuje operację odczytu i zapisu, aby zastąpić przechowywaną wartość  **\*tej** wartości wartością bitową i *wartość* oraz bieżącą wartość przechowywaną w  **\*tym**zakresie w ramach ograniczeń `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_or_eq"></a>niepodzielna:&#124;: operator =

Wykonuje wartość bitową lub dla określonej wartości i wartości  **\*przechowywanej.** Używane tylko przez całkowitą specjalizację.

```cpp
atomic<Ty>::operator|= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator|= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Parametry

*Wartościami*\
Wartość typu *ty*.

### <a name="return-value"></a>Wartość zwracana

Wynik bitowy lub.

### <a name="remarks"></a>Uwagi

Ten operator wykonuje operację odczytu i zapisu, aby zastąpić przechowywaną wartość  **\*tej** wartości wartością bitową lub *wartość* oraz bieżącą wartość przechowywaną w  **\*tym**zakresie w ramach ograniczeń `memory_order_seq_cst`ograniczenia [memory_order](atomic-enums.md) .

## <a name="op_xor_eq"></a>niepodzielna:: operator ^ =

Wykonuje bitowe wykluczające lub na określoną wartość oraz przechowywaną  **\*wartość.** Używane tylko przez całkowitą specjalizację.

```cpp
atomic<Ty>::operator^= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator^= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Parametry

*Wartościami*\
Wartość typu *ty*.

### <a name="return-value"></a>Wartość zwracana

Wynik bitowy wyłącznych lub.

### <a name="remarks"></a>Uwagi

Ten operator wykonuje operację odczytu i zapisu, aby zastąpić przechowywaną wartość  **\*tego** elementu wartością bitową wykluczającą lub *, a bieżącą* wartość przechowywaną w  **\*tym**miejscu w ramach ograniczeń `memory_order_seq_cst` ograniczenia [memory_order](atomic-enums.md) .

## <a name="compare_exchange_strong"></a>niepodzielna:: compare_exchange_strong

Wykonuje w  **\*tym**celu niepodzielną operację porównania i wymiany.

```cpp
bool compare_exchange_strong(
   Ty& Exp,
   Ty Value,
   memory_order Order1,
   memory_order Order2
) volatile noexcept;
bool compare_exchange_strong(
   Ty& Exp,
   Ty Value,
   memory_order Order1,
   memory_order Order2
) noexcept;
bool compare_exchange_strong(
   Ty& Exp,
   Ty Value,
   memory_order Order1 = memory_order_seq_cst
) volatile noexcept;
bool compare_exchange_strong(
   Ty& Exp,
   Ty Value,
   memory_order Order1 = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Parametry

*EXP*\
Wartość typu *ty*.

*Wartościami*\
Wartość typu *ty*.

*Order1*\
Pierwszy `memory_order` argument.

*Order2*\
Drugi `memory_order` argument.

### <a name="return-value"></a>Wartość zwracana

Wartość **logiczna** , która wskazuje wynik porównania wartości.

### <a name="remarks"></a>Uwagi

Ta niepodzielna operacja porównania i wymiany porównuje wartość przechowywaną w  **\*tym** elemencie z *EXP*. Jeśli wartości są równe, operacja zastępuje wartość, która jest przechowywana w  **\*tym** elemencie z *wartością* przy użyciu operacji odczytu-modify-write i stosując ograniczenia zlecenia pamięci, które są określone przez *Order1*. Jeśli wartości nie są równe, operacja używa wartości przechowywanej w  **\*tym** elemencie, aby zastąpić polecenie *EXP* i zastosować ograniczenia kolejności pamięci, które są określone przez *Order2*.

Przeciążenia, które nie mają sekundy `memory_order` , używają niejawnego *Order2* , który jest oparty na wartości *Order1*. Jeśli *Order1* jest `memory_order_acq_rel`, *Order2* jest `memory_order_acquire`. Jeśli *Order1* jest `memory_order_release`, *Order2* jest `memory_order_relaxed`. We wszystkich innych przypadkach *Order2* jest równa *Order1*.

W przypadku przeciążeń `memory_order` przyjmujących dwa parametry wartość *Order2* nie może być `memory_order_release` lub `memory_order_acq_rel`i nie może być silniejszy niż wartość *Order1*.

## <a name="compare_exchange_weak"></a>niepodzielna:: compare_exchange_weak

Wykonuje na  **\*tym**samym słabą niepodzielną operację porównania i wymiany.

```cpp
bool compare_exchange_weak(
   Ty& Exp,
   Ty Value,
   memory_order Order1,
   memory_order Order2
) volatile noexcept;
bool compare_exchange_weak(
   Ty& Exp,
   Ty Value,
   memory_order Order1,
   memory_order Order2
) noexcept;
bool compare_exchange_weak(
   Ty& Exp,
   Ty Value,
   memory_order Order1 = memory_order_seq_cst
) volatile noexcept;
bool compare_exchange_weak(
   Ty& Exp,
   Ty Value,
   memory_order Order1 = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Parametry

*EXP*\
Wartość typu *ty*.

*Wartościami*\
Wartość typu *ty*.

*Order1*\
Pierwszy `memory_order` argument.

*Order2*\
Drugi `memory_order` argument.

### <a name="return-value"></a>Wartość zwracana

Wartość **logiczna** , która wskazuje wynik porównania wartości.

### <a name="remarks"></a>Uwagi

Ta niepodzielna operacja porównania i wymiany porównuje wartość przechowywaną w  **\*tym** elemencie z *EXP*. Jeśli wartości są równe, operacja zastępuje wartość, która jest przechowywana w  **\*tym** elemencie z*wartością* przy użyciu operacji odczytu-modify-write i stosując ograniczenia zlecenia pamięci, które są określone przez *Order1*. Jeśli wartości nie są równe, operacja używa wartości przechowywanej w  **\*tym** elemencie, aby zastąpić polecenie *EXP* i zastosować ograniczenia kolejności pamięci, które są określone przez *Order2*.

Słaba, niepodzielna operacja porównania i wymiany wykonuje wymianę, jeśli porównywane wartości są równe. Jeśli wartości nie są równe, operacja nie jest gwarantowana do wykonania wymiany.

Przeciążenia, które nie mają sekundy `memory_order` , używają niejawnego *Order2* , który jest oparty na wartości *Order1*. Jeśli *Order1* jest `memory_order_acq_rel`, *Order2* jest `memory_order_acquire`. Jeśli *Order1* jest `memory_order_release`, *Order2* jest `memory_order_relaxed`. We wszystkich innych przypadkach *Order2* jest równa *Order1*.

W przypadku przeciążeń `memory_order` przyjmujących dwa parametry wartość *Order2* nie może być `memory_order_release` lub `memory_order_acq_rel`i nie może być silniejszy niż wartość *Order1*.

## <a name="exchange"></a>niepodzielna:: Exchange

Używa określonej wartości w celu zastąpienia przechowywanej wartości  **\*tego**elementu.

```cpp
Ty atomic<Ty>::exchange(
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::exchange(
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Parametry

*Wartościami*\
Wartość typu *ty*.

*Porządek*\
A `memory_order`.

### <a name="return-value"></a>Wartość zwracana

Wartość przechowywana  **\*tego** elementu przed wymianą.

### <a name="remarks"></a>Uwagi

Ta operacja wykonuje operację odczytu/modyfikacji i zapisu, aby zastąpić  wartość przechowywaną w  **\*tym**elemencie w ramach ograniczeń pamięci określonych przez *kolejność*.

## <a name="fetch_add"></a>niepodzielna:: fetch_add

Pobiera wartość przechowywaną w  **\*tym**elemencie, a następnie dodaje określoną wartość do przechowywanej wartości.

```cpp
Ty atomic<Ty>::fetch_add (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_add (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Parametry

*Wartościami*\
Wartość typu *ty*.

*Porządek*\
A `memory_order`.

### <a name="return-value"></a>Wartość zwracana

Obiekt *ty* , który zawiera wartość przechowywaną w  **\*tym** elemencie przed dodaniem.

### <a name="remarks"></a>Uwagi

Metoda wykonuje operację odczytu i modyfikacji zapisu, *Aby dodać* niepodzielną wartość do wartości przechowywanej w  **\*tym**miejscu i stosuje ograniczenia pamięci, które są określone przez *kolejność.* `fetch_add`

## <a name="fetch_and"></a>niepodzielna:: fetch_and

Wykonuje wartości bitowe i na wartość oraz istniejącą wartość, która jest przechowywana w  **\*tym**elemencie.

```cpp
Ty atomic<Ty>::fetch_and (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_and (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Parametry

*Wartościami*\
Wartość typu *ty*.

*Porządek*\
A `memory_order`.

### <a name="return-value"></a>Wartość zwracana

Obiekt *ty* , który zawiera wynik bitowy i.

### <a name="remarks"></a>Uwagi

Metoda wykonuje operację odczytu i modyfikacji zapisu, aby zastąpić przechowywaną  **\*wartość tego** elementu wartością bitową i *wartość* oraz bieżącą wartość przechowywaną w  **\*tym**miejscu w pamięci. `fetch_and` ograniczenia, które są określone przez *kolejność*.

## <a name="fetch_or"></a>niepodzielna:: fetch_or

Wykonuje wartość bitową lub wartości i istniejącą wartość, która jest przechowywana w  **\*tym**elemencie.

```cpp
Ty atomic<Ty>::fetch_or (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_or (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Parametry

*Wartościami*\
Wartość typu *ty*.

*Porządek*\
A `memory_order`.

### <a name="return-value"></a>Wartość zwracana

Obiekt *ty* , który zawiera wynik bitowy lub.

### <a name="remarks"></a>Uwagi

Metoda wykonuje operację odczytu/modyfikacji i zapisu, aby zastąpić przechowywaną  **\*wartość tego** elementu *wartością* bitową lub wartość oraz bieżącą wartość przechowywaną w  **\*tym**miejscu w pamięci. `fetch_or` ograniczenia, które są określone przez *kolejność*.

## <a name="fetch_sub"></a>niepodzielna:: fetch_sub

Odejmuje określoną wartość z przechowywanej wartości.

```cpp
Ty atomic<Ty>::fetch_sub (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_sub (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Parametry

*Wartościami*\
Wartość typu *ty*.

*Porządek*\
A `memory_order`.

### <a name="return-value"></a>Wartość zwracana

Obiekt *ty* , który zawiera wynik odejmowania.

### <a name="remarks"></a>Uwagi

Metoda wykonuje operację odczytu i modyfikacji zapisu w *celu odejmowania* niepodzielnych wartości z wartości przechowywanej w  **\*tym**miejscu w ramach ograniczeń pamięci, które są określone przez *kolejność.* `fetch_sub`

## <a name="fetch_xor"></a>niepodzielna:: fetch_xor

Wykonuje bitowe wartościowe lub na wartość i istniejącą wartość, która jest przechowywana w  **\*tym**elemencie.

```cpp
Ty atomic<Ty>::fetch_xor (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_xor (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Parametry

*Wartościami*\
Wartość typu *ty*.

*Porządek*\
A `memory_order`.

### <a name="return-value"></a>Wartość zwracana

Obiekt *ty* zawierający wynik bitowe wyłącznych lub.

### <a name="remarks"></a>Uwagi

Metoda wykonuje operację odczytu/modyfikacji i zapisu, aby zastąpić przechowywaną  **\*wartość tego** elementu wartością bitową wykluczającą lub, *a bieżącą* wartość przechowywaną w  **\*tym**miejscu i stosuje `fetch_xor` ograniczenia pamięci, które są określone w *kolejności*.

## <a name="is_lock_free"></a>niepodzielna:: is_lock_free

Określa, czy operacje niepodzielne w  **\*tej** usłudze są wolne od blokady.

```cpp
bool is_lock_free() const volatile noexcept;
```

### <a name="return-value"></a>Wartość zwracana

prawda, jeśli operacje niepodzielne na  **\*tym** serwerze są wolne od blokady; w przeciwnym razie, FAŁSZ.

### <a name="remarks"></a>Uwagi

Typ niepodzielny jest zablokowany, jeśli żadna niepodzielna operacja nie używa blokad.

## <a name="load"></a>niepodzielna:: Load

Pobiera wartość przechowywaną w  **\*ramach**określonych ograniczeń pamięci.

```cpp
Ty atomic::load(
   memory_order Order = memory_order_seq_cst
) const volatile noexcept;
Ty atomic::load(
   memory_order Order = memory_order_seq_cst
) const noexcept;
```

### <a name="parameters"></a>Parametry

*Porządek*\
A `memory_order`. *Kolejność* nie może być `memory_order_release` lub `memory_order_acq_rel`.

### <a name="return-value"></a>Wartość zwracana

Pobrana wartość, która jest przechowywana w  **\*tym**elemencie.

## <a name="store"></a>niepodzielna:: Store

Przechowuje określoną wartość.

```cpp
void atomic<Ty>::store(
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
void atomic<Ty>::store(
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>Parametry

*Wartościami*\
Obiekt *ty* .

*Porządek*\
`memory_order` Ograniczenie.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego przechowuje niepodzielną *wartość* w `*this`, w ramach ograniczeń pamięci, które są określone przez *kolejność*.

## <a name="see-also"></a>Zobacz także

[\<> niepodzielne](../standard-library/atomic.md)\
[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)
