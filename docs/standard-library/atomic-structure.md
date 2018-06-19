---
title: Atomic — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/20/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- atomic/std::atomic
dev_langs:
- C++
ms.assetid: 261628ed-7049-41ac-99b9-cfe49f696b44
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7308c127bebd2185429509315ebafb3d83a7efea
ms.sourcegitcommit: b0d5557dbb57128da560a0a4634312ec4a050a90
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2018
ms.locfileid: "34476110"
---
# <a name="atomic-structure"></a>atomic — Struktura

Zawiera opis obiektu, który wykonuje niepodzielne operacje na przechowywana wartość typu *Ty*.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct atomic;
```

## <a name="members"></a>Elementy członkowskie

|Element członkowski|Opis|
|----------|-----------------|
|**Konstruktor**||
|[atomic](#atomic)|Tworzy obiekt atomic.|
|**Operatory**||
|[Atomic::operator Ty](#op_ty)|Odczytuje i zwraca wartość przechowywana. ([atomic::load](#load))|
|[Atomic::operator =](#op_eq)|Używa określonej wartości w celu zastąpienia przechowywanej wartości. ([atomic::store](#store))|
|[Atomic::operator ++](#op_inc)|Zwiększa wartość przechowywana. Używany tylko przez specjalizacje całkowite i wskaźnika.|
|[Atomic::operator +=](#op_add_eq)|Dodaje określoną wartość do przechowywanej wartości. Używany tylko przez specjalizacje całkowite i wskaźnika.|
|[Atomic::operator--](#op_dec)|Zmniejsza przechowywanej wartości. Używany tylko przez specjalizacje całkowite i wskaźnika.|
|[Atomic::operator-=](#op_sub_eq)|Odejmuje określoną wartość z wartością przechowywaną. Używany tylko przez specjalizacje całkowite i wskaźnika.|
|[Atomic::operator & =](#op_and_eq)|Wykonuje bitowej określoną wartość i przechowywana wartość. Używany tylko przez specjalizacje wartości całkowitych.|
|[Atomic::operator&#124;=](#op_or_eq)|Wykonuje bitowej lub określoną wartość i przechowywana wartość. Używany tylko przez specjalizacje wartości całkowitych.|
|[Atomic::operator ^ =](#op_xor_eq)|Operator wyłączny wykonuje lub określoną wartość i przechowywana wartość. Używany tylko przez specjalizacje wartości całkowitych.|
|**Funkcje**||
|[compare_exchange_strong](#compare_exchange_strong)|Wykonuje *atomic_compare_and_exchange* operacji na **to** i zwraca wynik.|
|[compare_exchange_weak](#compare_exchange_weak)|Wykonuje *weak_atomic_compare_and_exchange* operacji na **to** i zwraca wynik.|
|[fetch_add](#fetch_add)|Dodaje określoną wartość do przechowywanej wartości.|
|[fetch_and](#fetch_and)|Wykonuje bitowej określoną wartość i przechowywana wartość.|
|[fetch_or](#fetch_or)|Wykonuje bitowej lub określoną wartość i przechowywana wartość.|
|[fetch_sub](#fetch_sub)|Odejmuje określoną wartość z wartością przechowywaną.|
|[fetch_xor](#fetch_xor)|Operator wyłączny wykonuje lub określoną wartość i przechowywana wartość.|
|[is_lock_free](#is_lock_free)|Określa, czy niepodzielne operacje na **to** są *nieblokującą*. Jest typem niepodzielnym *nieblokującą* blokad użycie żadne niepodzielne operacje tego typu.|
|[Obciążenia](#load)|Odczytuje i zwraca wartość przechowywana.|
|[Magazyn](#store)|Używa określonej wartości w celu zastąpienia przechowywanej wartości.|

## <a name="remarks"></a>Uwagi

Typ *Ty* musi być *trivially copyable*. Oznacza to, za pomocą [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) Aby kopiować bajty jego musi mieć prawidłową *Ty* obiekt, który porównuje taki sam jak oryginalny obiekt. [Compare_exchange_weak](#compare_exchange_weak) i [compare_exchange_strong](#compare_exchange_strong) Użyj funkcje Członkowskie [funkcji memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md) do ustalenia, czy dwa *Ty* wartości są takie same. Te funkcje nie będą używać *Ty*— definicja **operator ==**. Funkcje Członkowskie **atomic** użyj **memcpy** można skopiować wartości typu *Ty*.

Częściowa specjalizacja, **atomic\<Ty \* >** , istnieje dla wszystkich typów wskaźnika. Specjalizacja umożliwia dodanie przesunięcia wartości wskaźnika zarządzanych lub odejmowania przesunięcie od niego. Operacje arytmetyczne przyjmuje argumentu typu **ptrdiff_t —** i dostosować ten argument na podstawie rozmiaru *Ty* aby były spójne z adresem zwykłej arytmetyczne.

Dla każdego typu całkowitego, z wyjątkiem istnieje specjalizacji **bool**. Każdy specjalizacji zawiera bogaty zestaw metod niepodzielne operacje arytmetyczne i logicznych.

||||
|-|-|-|
|**Atomic\<char >**|**Atomic\<podpisany char >**|**Atomic\<unsigned char >**|
|**Atomic\<char16_t >**|**Atomic\<char32_t >**|**Atomic\<wchar_t >**|
|**Atomic\<krótkich >**|**Atomic\<niepodpisane krótko >**|**Atomic\<int >**|
|**Atomic\<unsigned int >**|**Atomic\<długi >**|**Atomic\<unsigned long >**|
|**Atomic\<długi czas >**|**Atomic\<unsigned long long >**|

Całkowite specjalizacje pochodzą od odpowiadającego **atomic_integral** typów. Na przykład **atomic\<unsigned int >** jest pochodną **atomic_uint**.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<atomic >

**Namespace:** Standard

## <a name="atomic"></a> Atomic::Atomic —

Tworzy obiekt atomic.

```cpp
atomic();
atomic( const atomic& );
atomic( Ty Value ) noexcept;
```

### <a name="parameters"></a>Parametry

*Wartość*<br/>
Wartość inicjowania.

### <a name="remarks"></a>Uwagi

Atomic obiektów nie można skopiować lub przenieść.

Obiekty, które są wystąpieniami atomic\<*Ty*> mogą być inicjowane tylko przez konstruktora, który przyjmuje argument typu *Ty* i nie przy użyciu inicjowania agregacji. Jednak atomic_integral obiekty mogą być inicjowane tylko przy użyciu inicjowania agregacji.

```cpp
atomic<int> ai0 = ATOMIC_VAR_INIT(0);
atomic<int> ai1(0);
```

## <a name="op_ty"></a> Atomic::operator *Ty*

Operator dla typu określonego w szablonie atomic\<*Ty*>. Pobiera wartość przechowywanych w  **\*to**.

```cpp
atomic<Ty>::operator Ty() const volatile noexcept;
atomic<Ty>::operator Ty() const noexcept;
```

### <a name="remarks"></a>Uwagi

Zastosowanie tego operatora **memory_order_seq_cst** [memory_order](atomic-enums.md).

## <a name="op_eq"></a> Atomic::operator =

Zapisuje określoną wartość.

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

Zwiększa wartość przechowywana. Używany tylko przez specjalizacje całkowite i wskaźnika.

```cpp
Ty atomic<Ty>::operator++(int) volatile noexcept;
Ty atomic<Ty>::operator++(int) noexcept;
Ty atomic<Ty>::operator++() volatile noexcept;
Ty atomic<Ty>::operator++() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Pierwsze dwa operatory zwracają wartość zwiększany; ostatnie dwa operatory zwracają wartość przed przyrostu. Operatorzy **memory_order_seq_cst** [memory_order](atomic-enums.md).

## <a name="op_add_eq"></a> Atomic::operator +=

Dodaje określoną wartość do przechowywanej wartości. Używany tylko przez specjalizacje całkowite i wskaźnika.

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

A *Ty* obiekt zawierający wynik operacji dodawania.

### <a name="remarks"></a>Uwagi

Używa tego operatora **memory_order_seq_cst** [memory_order](atomic-enums.md).

## <a name="op_dec"></a> Atomic::operator--

Zmniejsza przechowywanej wartości. Używany tylko przez specjalizacje całkowite i wskaźnika.

```cpp
Ty atomic<Ty>::operator--(int) volatile noexcept;
Ty atomic<Ty>::operator--(int) noexcept;
Ty atomic<Ty>::operator--() volatile noexcept;
Ty atomic<Ty>::operator--() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Pierwsze dwa operatory zwracają wartość zmniejszany; ostatnie dwa operatory zwracają wartość przed zmniejszenie. Operatorzy **memory_order_seq_cst** [memory_order](atomic-enums.md).

## <a name="op_sub_eq"></a> Atomic::operator-=

Odejmuje określoną wartość z wartością przechowywaną. Używany tylko przez specjalizacje całkowite i wskaźnika.

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

A *Ty* obiekt zawierający wynik odejmowania.

### <a name="remarks"></a>Uwagi

Używa tego operatora **memory_order_seq_cst** [memory_order](atomic-enums.md).

## <a name="op_and_eq"></a> Atomic::operator & =

Wykonuje bitowej i o określonej wartości i przechowywana wartość  **\*to**. Używany tylko przez specjalizacje wartości całkowitych.

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

Wynik operatora testu koniunkcji i.

### <a name="remarks"></a>Uwagi

Ten operator wykonuje operację read-modify-write zastąpić przechowywana wartość  **\*to** z bitowego i *wartość* i bieżąca wartość, która jest przechowywana w  **\*to**, zgodnie z ograniczeniami **memory_order_seq_cst** [memory_order](atomic-enums.md).

## <a name="op_or_eq"></a> Atomic::operator&#124;=

Wykonuje bitowej lub na określoną wartość i przechowywana wartość  **\*to**. Używany tylko przez specjalizacje wartości całkowitych.

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

Wynik operatora testu koniunkcji lub.

### <a name="remarks"></a>Uwagi

Ten operator wykonuje operację read-modify-write zastąpić przechowywana wartość  **\*to** z bitowego lub *wartość* i bieżąca wartość, która jest przechowywana w  **\*to**, zgodnie z ograniczeniami **memory_order_seq_cst** [memory_order](atomic-enums.md) ograniczenia.

## <a name="op_xor_eq"></a> Atomic::operator ^ =

Operator wyłączny wykonuje lub na określoną wartość i przechowywana wartość  **\*to**. Używany tylko przez specjalizacje wartości całkowitych.

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

Wynik operator wyłączny lub.

### <a name="remarks"></a>Uwagi

Ten operator wykonuje operację read-modify-write zastąpić przechowywana wartość  **\*to** z bitowego wyłącznie lub *wartość* i bieżąca wartość, która jest przechowywana w  **\*to**, zgodnie z ograniczeniami **memory_order_seq_cst** [memory_order](atomic-enums.md) ograniczenia.

## <a name="compare_exchange_strong"></a> Atomic::compare_exchange_strong

Wykonuje operację atomic Porównaj i programu exchange na  **\*to**.

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
Pierwszy **memory_order** argumentu.

*Order2*<br/>
Drugi **memory_order** argumentu.

### <a name="return-value"></a>Wartość zwracana

A **bool** wskazująca wynik porównania wartości.

### <a name="remarks"></a>Uwagi

Operacja atomic porównania i exchange porównuje wartości, który jest przechowywany w  **\*to** z *Exp*. Jeśli wartości są równe, operacja zastąpi wartość, która jest przechowywana w  **\*to** z *wartość* przy użyciu operacji read-modify-write i stosując ograniczenia kolejności pamięci, które są określony przez *Order1*. Jeśli wartości nie są takie same, operacja używa wartości, który jest przechowywany w  **\*to** zastąpić *Exp* i stosuje ograniczenia kolejności pamięci, które są określone przez *Order2* .

Przeciążenia, które nie mają drugiej **memory_order** Użyj niejawny *Order2* opartego na wartość *Order1*. Jeśli *Order1* jest **memory_order_acq_rel**, *Order2* jest **memory_order_acquire**. Jeśli *Order1* jest **memory_order_release**, *Order2* jest **memory_order_relaxed**. We wszystkich innych przypadkach *Order2* jest równa *Order1*.

Dla przeciążeń, które przyjmują dwa **memory_order** parametrów, wartość *Order2* nie może być **memory_order_release** lub **memory_order_acq_rel**i nie może być mocniejszy niż wartość *Order1*.

## <a name="compare_exchange_weak"></a> Atomic::compare_exchange_weak

Operacja wykonywana przez słabe atomic Porównaj i programu exchange na  **\*to**.

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
Pierwszy **memory_order** argumentu.

*Order2*<br/>
Drugi **memory_order** argumentu.

### <a name="return-value"></a>Wartość zwracana

A **bool** wskazująca wynik porównania wartości.

### <a name="remarks"></a>Uwagi

Operacja atomic porównania i exchange porównuje wartości, który jest przechowywany w  **\*to** z *Exp*. Jeśli wartości są równe, operacja zastąpi wartość, która jest przechowywana w  **\*to** z*wartość* przy użyciu operacji read-modify-write i stosując ograniczenia kolejności pamięci, które są określony przez *Order1*. Jeśli wartości nie są takie same, operacja używa wartości, który jest przechowywany w  **\*to** zastąpić *Exp* i stosuje ograniczenia kolejności pamięci, które są określone przez *Order2* .

Niska atomic porównania i operacji wymiana wykonuje programu exchange, jeśli porównaniu wartości są równe. Jeśli wartości nie są takie same, operacja nie jest gwarantowana do wykonania programu exchange.

Przeciążenia, które nie mają drugiej **memory_order** Użyj niejawny *Order2* opartego na wartość *Order1*. Jeśli *Order1* jest **memory_order_acq_rel**, *Order2* jest **memory_order_acquire**. Jeśli *Order1* jest **memory_order_release**, *Order2* jest **memory_order_relaxed**. We wszystkich innych przypadkach *Order2* jest równa *Order1*.

Dla przeciążeń, które przyjmują dwa **memory_order** parametrów, wartość *Order2* nie może być **memory_order_release** lub **memory_order_acq_rel**i nie może być mocniejszy niż wartość *Order1*.

## <a name="exchange"></a> Atomic::Exchange

Używa określonej wartości w celu zastąpienia przechowywana wartość  **\*to**.

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
A **memory_order**.

### <a name="return-value"></a>Wartość zwracana

Przechowywana wartość  **\*to** przed programu exchange.

### <a name="remarks"></a>Uwagi

Tę operację wykonuje operację read-modify-write do użycia *wartość* zastąpić wartość, która jest przechowywana w  **\*to**, w ramach ograniczeń pamięci, które są określone przez  *Kolejność*.

## <a name="fetch_add"></a> Atomic::fetch_add

Pobiera wartość przechowywana we  **\*to**, a następnie dodaje określoną wartość do wartości przechowywanej.

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
A **memory_order**.

### <a name="return-value"></a>Wartość zwracana

A *Ty* obiekt, który zawiera wartości przechowywanej w  **\*to** przed dodaniem.

### <a name="remarks"></a>Uwagi

**Fetch_add** metoda wykonuje operację read-modify-write, aby automatycznie dodać *wartość* do wartości przechowywanej w  **\*to**i stosuje pamięci ograniczenia, które są określone przez *kolejności*.

## <a name="fetch_and"></a> Atomic::fetch_and

Wykonuje bitowej i na wartość i istniejącą wartość, która jest przechowywana w  **\*to**.

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
A **memory_order**.

### <a name="return-value"></a>Wartość zwracana

A *Ty* obiekt zawierający wynik operatora testu koniunkcji i.

### <a name="remarks"></a>Uwagi

**Fetch_and** metoda wykonuje operację read-modify-write zastąpić przechowywana wartość  **\*to** z bitowego i *wartość* i bieżącego wartość, która jest przechowywana w  **\*to**, w ramach ograniczeń pamięci, które są określone przez *kolejności*.

## <a name="fetch_or"></a> Atomic::fetch_or

Wykonuje bitowej lub na wartość i istniejącą wartość, która jest przechowywana w  **\*to**.

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
A **memory_order**.

### <a name="return-value"></a>Wartość zwracana

A *Ty* obiekt zawierający wynik operatora testu koniunkcji lub.

### <a name="remarks"></a>Uwagi

**Fetch_or** metoda wykonuje operację read-modify-write zastąpić przechowywana wartość  **\*to** z bitowego lub *wartość* i bieżącą wartość jest przechowywana w  **\*to**, w ramach ograniczeń pamięci, które są określone przez *kolejności*.

## <a name="fetch_sub"></a> Atomic::fetch_sub

Odejmuje określoną wartość z wartością przechowywaną.

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
A **memory_order**.

### <a name="return-value"></a>Wartość zwracana

A *Ty* obiekt zawierający wynik odejmowania.

### <a name="remarks"></a>Uwagi

**Fetch_sub** metoda wykonuje operację read-modify-write do odjęcia atomowo *wartość* z wartością przechowywaną w  **\*to**, w pamięci ograniczenia, które są określone przez *kolejności*.

## <a name="fetch_xor"></a> Atomic::fetch_xor

Operator wyłączny wykonuje lub na wartość i istniejącą wartość, która jest przechowywana w  **\*to**.

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
A **memory_order**.

### <a name="return-value"></a>Wartość zwracana

A *Ty* obiekt zawierający wynik operator wyłączny lub.

### <a name="remarks"></a>Uwagi

**Fetch_xor** metoda wykonuje operację read-modify-write zastąpić przechowywana wartość  **\*to** z bitowego wyłącznie lub *wartość* i Bieżąca wartość, która jest przechowywana w  **\*to**i stosuje ograniczenia pamięci, które są określone przez *kolejności*.

## <a name="is_lock_free"></a> Atomic::is_lock_free

Określa, czy niepodzielne operacje na  **\*to** są nieblokującą.

```cpp
bool is_lock_free() const volatile noexcept;
```

### <a name="return-value"></a>Wartość zwracana

wartość true, jeśli jest to niepodzielne operacje na  **\*to** są blokady bezpłatne, w przeciwnym razie wartość false.

### <a name="remarks"></a>Uwagi

Typem niepodzielnym jest nieblokującą blokad użycie żadne niepodzielne operacje tego typu.

## <a name="load"></a> Atomic::Load

Pobiera wartość przechowywanych w  **\*to**, w ramach ograniczeń określonych pamięci.

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
A **memory_order**. *Kolejność* nie może być **memory_order_release** lub **memory_order_acq_rel**.

### <a name="return-value"></a>Wartość zwracana

Pobrana wartość, która jest przechowywana w  **\*to**.

## <a name="store"></a> Atomic::store

Zapisuje określoną wartość.

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
A **memory_order** ograniczenia.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska automatycznie przechowuje *wartość* w `*this`, w ramach ograniczeń pamięci, które są określone przez *kolejności*.

## <a name="see-also"></a>Zobacz także

[\<niepodzielne >](../standard-library/atomic.md)<br/>
[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
