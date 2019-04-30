---
title: atomic — Struktura
ms.date: 04/20/2018
f1_keywords:
- atomic/std::atomic
ms.assetid: 261628ed-7049-41ac-99b9-cfe49f696b44
ms.openlocfilehash: 258812f033d34f040d96847581d6f51692a933b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62376672"
---
# <a name="atomic-structure"></a>atomic — Struktura

Opisuje obiekt, który wykonuje niepodzielne operacje na przechowywanej wartości typu *Ty*.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct atomic;
```

## <a name="members"></a>Elementy członkowskie

|Element członkowski|Opis|
|----------|-----------------|
|**Konstruktor**||
|[atomic](#atomic)|Tworzy anatomiczny obiekt.|
|**Operatory**||
|[Atomic::operator Ty](#op_ty)|Odczytuje i zwraca przechowywaną wartość. ([Atomic::Load —](#load))|
|[Atomic::operator =](#op_eq)|Używa określonej wartości, aby zastąpić przechowywaną wartość. ([Atomic::store —](#store))|
|[Atomic::operator ++](#op_inc)|Zwiększa przechowywaną wartość. Używane tylko przez liczbę całkowitą i wskaźnik specjalizacji.|
|[atomic::operator+=](#op_add_eq)|Dodaje określoną wartość do przechowywanej wartości. Używane tylko przez liczbę całkowitą i wskaźnik specjalizacji.|
|[atomic::operator--](#op_dec)|Dekrementuje przechowywaną wartość. Używane tylko przez liczbę całkowitą i wskaźnik specjalizacji.|
|[atomic::operator-=](#op_sub_eq)|Odejmuje określoną wartość z przechowywanej wartości. Używane tylko przez liczbę całkowitą i wskaźnik specjalizacji.|
|[Atomic::operator & =](#op_and_eq)|Wykonuje bitową operację i na określoną wartość i przechowywana wartość. Używane tylko przez liczbę całkowitą specjalizacji.|
|[Atomic::operator&#124;=](#op_or_eq)|Wykonuje bitową operację lub na określoną wartość i przechowywana wartość. Używane tylko przez liczbę całkowitą specjalizacji.|
|[Atomic::operator ^ =](#op_xor_eq)|Wykonuje wyłączny sumy bitowej lub na określoną wartość i przechowywana wartość. Używane tylko przez liczbę całkowitą specjalizacji.|
|**Funkcje**||
|[compare_exchange_strong](#compare_exchange_strong)|Wykonuje *atomic_compare_and_exchange* operacja **to** i zwraca wynik.|
|[compare_exchange_weak](#compare_exchange_weak)|Wykonuje *weak_atomic_compare_and_exchange* operacja **to** i zwraca wynik.|
|[fetch_add](#fetch_add)|Dodaje określoną wartość do przechowywanej wartości.|
|[fetch_and](#fetch_and)|Wykonuje bitową operację i na określoną wartość i przechowywana wartość.|
|[fetch_or](#fetch_or)|Wykonuje bitową operację lub na określoną wartość i przechowywana wartość.|
|[fetch_sub](#fetch_sub)|Odejmuje określoną wartość z przechowywanej wartości.|
|[fetch_xor](#fetch_xor)|Wykonuje wyłączny sumy bitowej lub na określoną wartość i przechowywana wartość.|
|[is_lock_free](#is_lock_free)|Określa, czy niepodzielne operacje na **to** są *wolne od blokady*. Typ niepodzielny *wolne od blokady* Jeśli żadne operacje niepodzielne tego typu nie używają blokady.|
|[Obciążenia](#load)|Odczytuje i zwraca przechowywaną wartość.|
|[store](#store)|Używa określonej wartości, aby zastąpić przechowywaną wartość.|

## <a name="remarks"></a>Uwagi

Typ *Ty* musi być *trywialne*. Oznacza to, za pomocą [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) do skopiowania jego bajtów musi mieć prawidłowy *Ty* obiekt, który jest równy do oryginalnego obiektu. [Compare_exchange_weak](#compare_exchange_weak) i [compare_exchange_strong](#compare_exchange_strong) funkcje Członkowskie korzystają [memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md) do określenia, czy dwie *Ty* wartości są takie same. Te funkcje nie będą używać *Ty*-zdefiniowane `operator==`. Funkcje elementów członkowskich `atomic` użyj `memcpy` do kopiowania wartości typu *Ty*.

Częściowa specjalizacja **atomic\<Ty \* >** , istnieje dla wszystkich typów wskaźnika. Specjalizacja umożliwia dodanie wartości wskaźnika zarządzanych przesunięcia lub odejmowania przesunięcie od niego. Operacje arytmetyczne przyjmują argument typu `ptrdiff_t` i dostosowują ten argument, zgodnie z rozmiarem *Ty* aby był spójny ze zwykłymi arytmetycznymi adresami.

Istnieje specjalizacja, dla każdego integralnego typu z wyjątkiem **bool**. Każda specjalizacja zawiera bogaty zestaw metod dla niepodzielnych operacji arytmetycznych i logicznych.

||||
|-|-|-|
|**Atomic\<char >**|**Atomic\<podpisany char >**|**Atomic\<unsigned char >**|
|**Atomic\<char16_t >**|**atomic\<char32_t>**|**Atomic\<wchar_t >**|
|**Atomic\<krótki >**|**Atomic\<typ unsigned short >**|**Atomic\<int >**|
|**Atomic\<unsigned int >**|**Atomic\<długa >**|**Atomic\<unsigned long >**|
|**Atomic\<long long >**|**Atomic\<unsigned long long >**|

Integralne specjalizacje są uzyskiwane z odpowiednich `atomic_integral` typów. Na przykład **atomic\<unsigned int >** jest tworzony na podstawie `atomic_uint`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<atomic >

**Namespace:** standardowe

## <a name="atomic"></a> Atomic::Atomic —

Tworzy anatomiczny obiekt.

```cpp
atomic();
atomic( const atomic& );
atomic( Ty Value ) noexcept;
```

### <a name="parameters"></a>Parametry

*Wartość*<br/>
Wartość inicjalizacji.

### <a name="remarks"></a>Uwagi

Niepodzielne obiekty nie można skopiować lub przenieść.

Obiekty, które są wystąpieniami atomic\<*Ty*> mogą być inicjowane tylko przez konstruktora, który przyjmuje argument typu *Ty* a nie za pomocą inicjowania agregacji. Jednak atomic_integral obiekty mogą być inicjowane tylko przy użyciu inicjowania agregacji.

```cpp
atomic<int> ai0 = ATOMIC_VAR_INIT(0);
atomic<int> ai1(0);
```

## <a name="op_ty"></a> Atomic::operator *Ty*

Operator dla typu określonego w szablonie atomic\<*Ty*>. Pobiera wartość przechowywaną w  **\*to**.

```cpp
atomic<Ty>::operator Ty() const volatile noexcept;
atomic<Ty>::operator Ty() const noexcept;
```

### <a name="remarks"></a>Uwagi

Zastosowanie tego operatora `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_eq"></a> Atomic::operator =

Przechowuje określona wartość.

```cpp
Ty operator=(
   Ty Value
) volatile noexcept;
Ty operator=(
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Parametry

*Wartość*<br/>
A *Ty* obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca *wartość*.

## <a name="op_inc"></a> Atomic::operator ++

Zwiększa przechowywaną wartość. Używane tylko przez liczbę całkowitą i wskaźnik specjalizacji.

```cpp
Ty atomic<Ty>::operator++(int) volatile noexcept;
Ty atomic<Ty>::operator++(int) noexcept;
Ty atomic<Ty>::operator++() volatile noexcept;
Ty atomic<Ty>::operator++() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Pierwsze dwa operatory zwracają wartość zwiększona; ostatnie dwa operatory zwracają wartość przed wartością przyrostu. Użyj operatorów `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_add_eq"></a> Atomic::operator +=

Dodaje określoną wartość do przechowywanej wartości. Używane tylko przez liczbę całkowitą i wskaźnik specjalizacji.

```cpp
Ty atomic<Ty>::operator+=(
   Ty Value
) volatile noexcept;
Ty atomic<Ty>::operator+=(
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Parametry

*Wartość*<br/>
Wartość wartości całkowitej lub wskaźnika.

### <a name="return-value"></a>Wartość zwracana

A *Ty* obiekt, który zawiera wynik dodawania.

### <a name="remarks"></a>Uwagi

Ten operator używa `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_dec"></a> Atomic::operator--

Dekrementuje przechowywaną wartość. Używane tylko przez liczbę całkowitą i wskaźnik specjalizacji.

```cpp
Ty atomic<Ty>::operator--(int) volatile noexcept;
Ty atomic<Ty>::operator--(int) noexcept;
Ty atomic<Ty>::operator--() volatile noexcept;
Ty atomic<Ty>::operator--() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Pierwsze dwa operatory zwracają wartość zmniejszony; ostatnie dwa operatory zwracają wartość przed dekrementacji. Użyj operatorów `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_sub_eq"></a> Atomic::operator-=

Odejmuje określoną wartość z przechowywanej wartości. Używane tylko przez liczbę całkowitą i wskaźnik specjalizacji.

```cpp
Ty atomic<Ty>::operator-=(
   Ty Value
) volatile noexcept;
Ty atomic<Ty>::operator-=(
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Parametry

*Wartość*<br/>
Wartość wartości całkowitej lub wskaźnika.

### <a name="return-value"></a>Wartość zwracana

A *Ty* obiekt, który zawiera wynik odejmowania.

### <a name="remarks"></a>Uwagi

Ten operator używa `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_and_eq"></a> Atomic::operator & =

Wykonuje bitową operację i na określoną wartość i przechowywana wartość  **\*to**. Używane tylko przez liczbę całkowitą specjalizacji.

```cpp
atomic<Ty>::operator&= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator&= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Parametry

*Wartość*<br/>
Wartości typu *Ty*.

### <a name="return-value"></a>Wartość zwracana

Wynik zadania poziomu bitowego i.

### <a name="remarks"></a>Uwagi

Ten operator wykonuje operację odczytu modify-write, aby zastąpić przechowywaną wartość  **\*to** z bitowej i *wartość* i bieżącą wartość przechowywaną w  **\*to**, zgodnie z ograniczeniami `memory_order_seq_cst` [memory_order](atomic-enums.md).

## <a name="op_or_eq"></a> Atomic::operator&#124;=

Wykonuje bitową operację lub na określoną wartość i przechowywana wartość  **\*to**. Używane tylko przez liczbę całkowitą specjalizacji.

```cpp
atomic<Ty>::operator|= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator|= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Parametry

*Wartość*<br/>
Wartości typu *Ty*.

### <a name="return-value"></a>Wartość zwracana

Wynik zadania poziomu bitowego lub.

### <a name="remarks"></a>Uwagi

Ten operator wykonuje operację odczytu modify-write, aby zastąpić przechowywaną wartość  **\*to** wartością bitową, lub z *wartość* i bieżącą wartość przechowywaną w  **\*to**, zgodnie z ograniczeniami `memory_order_seq_cst` [memory_order](atomic-enums.md) ograniczenia.

## <a name="op_xor_eq"></a> Atomic::operator ^ =

Wykonuje wyłączny sumy bitowej lub na określoną wartość i przechowywana wartość  **\*to**. Używane tylko przez liczbę całkowitą specjalizacji.

```cpp
atomic<Ty>::operator^= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator^= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>Parametry

*Wartość*<br/>
Wartości typu *Ty*.

### <a name="return-value"></a>Wartość zwracana

Wynik wyłączny sumy bitowej lub.

### <a name="remarks"></a>Uwagi

Ten operator wykonuje operację odczytu modify-write, aby zastąpić przechowywaną wartość  **\*to** z wyłączny sumy bitowej lub *wartość* i bieżącą wartość przechowywaną w  **\*to**, zgodnie z ograniczeniami `memory_order_seq_cst` [memory_order](atomic-enums.md) ograniczenia.

## <a name="compare_exchange_strong"></a> Atomic::compare_exchange_strong —

Wykonuje niepodzielna operacja porównania i wymiany na  **\*to**.

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

*EXP*<br/>
Wartości typu *Ty*.

*Wartość*<br/>
Wartości typu *Ty*.

*Order1*<br/>
Pierwszy `memory_order` argumentu.

*Order2*<br/>
Drugi `memory_order` argumentu.

### <a name="return-value"></a>Wartość zwracana

A **bool** oznacza to wynik porównania wartości.

### <a name="remarks"></a>Uwagi

Niepodzielna operacja porównania i wymiany porównuje wartość, która jest przechowywana w  **\*to** z *Exp*. Jeśli wartości są równe, operacja zastępuje wartość, która jest przechowywana w  **\*to** z *wartość* przy użyciu operacji odczytu i modyfikowania zapisu i stosując ograniczenia zlecenia pamięci, które są określony przez *Order1*. Jeśli wartości nie są równe, operacja wykorzystuje wartość, która jest przechowywana w  **\*to** zastąpić *Exp* i stosuje ograniczenia zlecenia pamięci, które są określone przez *Order2* .

Przeciążenia, które nie mają drugiego `memory_order` używają ukrytego *Order2* opartego na wartość *Order1*. Jeśli *Order1* jest `memory_order_acq_rel`, *Order2* jest `memory_order_acquire`. Jeśli *Order1* jest `memory_order_release`, *Order2* jest `memory_order_relaxed`. We wszystkich innych przypadkach *Order2* jest równa *Order1*.

Dla przeciążeń, które pobierają dwa `memory_order` parametrów, wartość *Order2* nie może być `memory_order_release` lub `memory_order_acq_rel`i nie może być silniejszy niż wartość *Order1*.

## <a name="compare_exchange_weak"></a> Atomic::compare_exchange_weak —

Wykonuje słabe, niepodzielna operacja porównania i wymiany na  **\*to**.

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

*EXP*<br/>
Wartości typu *Ty*.

*Wartość*<br/>
Wartości typu *Ty*.

*Order1*<br/>
Pierwszy `memory_order` argumentu.

*Order2*<br/>
Drugi `memory_order` argumentu.

### <a name="return-value"></a>Wartość zwracana

A **bool** oznacza to wynik porównania wartości.

### <a name="remarks"></a>Uwagi

Niepodzielna operacja porównania i wymiany porównuje wartość, która jest przechowywana w  **\*to** z *Exp*. Jeśli wartości są równe, operacja zastępuje wartość, która jest przechowywana w  **\*to** z*wartość* przy użyciu operacji odczytu i modyfikowania zapisu i stosując ograniczenia zlecenia pamięci, które są określony przez *Order1*. Jeśli wartości nie są równe, operacja wykorzystuje wartość, która jest przechowywana w  **\*to** zastąpić *Exp* i stosuje ograniczenia zlecenia pamięci, które są określone przez *Order2* .

Porównanie atomowe ograniczymy i operacji wymiany wykonuje wymianę w przypadku porównane wartości są równe. Jeśli wartości nie są równe, działanie nie jest gwarantowane do wykonania wymiany.

Przeciążenia, które nie mają drugiego `memory_order` używają ukrytego *Order2* opartego na wartość *Order1*. Jeśli *Order1* jest `memory_order_acq_rel`, *Order2* jest `memory_order_acquire`. Jeśli *Order1* jest `memory_order_release`, *Order2* jest `memory_order_relaxed`. We wszystkich innych przypadkach *Order2* jest równa *Order1*.

Dla przeciążeń, które pobierają dwa `memory_order` parametrów, wartość *Order2* nie może być `memory_order_release` lub `memory_order_acq_rel`i nie może być silniejszy niż wartość *Order1*.

## <a name="exchange"></a> Atomic::Exchange —

Używa określonej wartości, aby zastąpić przechowywaną wartość  **\*to**.

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

*Wartość*<br/>
Wartości typu *Ty*.

*Kolejność*<br/>
A `memory_order`.

### <a name="return-value"></a>Wartość zwracana

Przechowywana wartość  **\*to** przed wymianą.

### <a name="remarks"></a>Uwagi

Ta operacja wykonuje operację odczytu modify-write używać *wartość* Aby zastąpić wartość, która jest przechowywana w  **\*to**, w ramach ograniczeń pamięci, które są określone przez  *Kolejność*.

## <a name="fetch_add"></a> Atomic::fetch_add —

Pobiera wartość przechowywaną w  **\*to**, a następnie dodaje określoną wartość do przechowywanej wartości.

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

*Wartość*<br/>
Wartości typu *Ty*.

*Kolejność*<br/>
A `memory_order`.

### <a name="return-value"></a>Wartość zwracana

A *Ty* obiekt, który zawiera wartość przechowywaną w  **\*to** przed dodaniem.

### <a name="remarks"></a>Uwagi

`fetch_add` Metoda wykonuje operację odczytu modify-write, aby przeprowadzić Dodawanie niepodzielne *wartość* do wartości przechowywanej w  **\*to**i stosuje ograniczenia pamięci, które są określone przez *Kolejności*.

## <a name="fetch_and"></a> Atomic::fetch_and —

Wykonuje bitową operację i na wartość i istniejącą wartość, która jest przechowywana w  **\*to**.

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

*Wartość*<br/>
Wartości typu *Ty*.

*Kolejność*<br/>
A `memory_order`.

### <a name="return-value"></a>Wartość zwracana

A *Ty* obiekt, który zawiera wynik bitowy i.

### <a name="remarks"></a>Uwagi

`fetch_and` Metoda wykonuje operację odczytu modify-write, aby zastąpić przechowywaną wartość  **\*to** z bitowej i *wartość* i bieżącą wartość przechowywaną w  **\*to**, w ramach ograniczeń pamięci, które są określone przez *kolejności*.

## <a name="fetch_or"></a> Atomic::fetch_or —

Wykonuje bitową operację lub na wartość i istniejącą wartość, która jest przechowywana w  **\*to**.

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

*Wartość*<br/>
Wartości typu *Ty*.

*Kolejność*<br/>
A `memory_order`.

### <a name="return-value"></a>Wartość zwracana

A *Ty* obiekt, który zawiera wynik bitowy lub.

### <a name="remarks"></a>Uwagi

`fetch_or` Metoda wykonuje operację odczytu modify-write, aby zastąpić przechowywaną wartość  **\*to** wartością bitową, lub z *wartość* i bieżącą wartość przechowywaną w  **\*to**, w ramach ograniczeń pamięci, które są określone przez *kolejności*.

## <a name="fetch_sub"></a> Atomic::fetch_sub —

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

*Wartość*<br/>
Wartości typu *Ty*.

*Kolejność*<br/>
A `memory_order`.

### <a name="return-value"></a>Wartość zwracana

A *Ty* obiekt, który zawiera wynik odejmowania.

### <a name="remarks"></a>Uwagi

`fetch_sub` Metoda wykonuje operację odczytu modify-write, aby przeprowadzić odejmowanie niepodzielne *wartość* z wartości przechowywanej w  **\*to**, w ramach ograniczeń pamięci, które są określone przez *Kolejności*.

## <a name="fetch_xor"></a> Atomic::fetch_xor —

Wykonuje wyłączny sumy bitowej lub na wartość i istniejącą wartość, która jest przechowywana w  **\*to**.

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

*Wartość*<br/>
Wartości typu *Ty*.

*Kolejność*<br/>
A `memory_order`.

### <a name="return-value"></a>Wartość zwracana

A *Ty* obiektu, który zawiera wynik wyłączny sumy bitowej lub.

### <a name="remarks"></a>Uwagi

`fetch_xor` Metoda wykonuje operację odczytu modify-write, aby zastąpić przechowywaną wartość  **\*to** z wyłączny sumy bitowej lub *wartość* i bieżącą wartość przechowywaną w  **\*to**i stosuje ograniczenia pamięci, które są określone przez *kolejności*.

## <a name="is_lock_free"></a> Atomic::is_lock_free —

Określa, czy niepodzielne operacje na  **\*to** są wolne od blokady.

```cpp
bool is_lock_free() const volatile noexcept;
```

### <a name="return-value"></a>Wartość zwracana

wartość true, jeśli jest to niepodzielne operacje na  **\*to** są blokady swobodnego; w przeciwnym razie wartość false.

### <a name="remarks"></a>Uwagi

Typ niepodzielny to wolne od blokady, jeśli żadne operacje niepodzielne tego typu nie używają blokady.

## <a name="load"></a> Atomic::Load —

Pobiera wartość przechowywaną w  **\*to**, w ramach określonych ograniczeń pamięci.

```cpp
Ty atomic::load(
   memory_order Order = memory_order_seq_cst
) const volatile noexcept;
Ty atomic::load(
   memory_order Order = memory_order_seq_cst
) const noexcept;
```

### <a name="parameters"></a>Parametry

*Kolejność*<br/>
A `memory_order`. *Kolejność* nie może być `memory_order_release` lub `memory_order_acq_rel`.

### <a name="return-value"></a>Wartość zwracana

Pobrana wartość, która jest przechowywana w  **\*to**.

## <a name="store"></a> Atomic::store —

Przechowuje określona wartość.

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

*Wartość*<br/>
A *Ty* obiektu.

*Kolejność*<br/>
A `memory_order` ograniczenia.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego niepodzielne przechowuje *wartość* w `*this`, w ramach ograniczeń pamięci, które są określone przez *kolejności*.

## <a name="see-also"></a>Zobacz także

[\<atomic>](../standard-library/atomic.md)<br/>
[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
