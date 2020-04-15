---
title: max_variable_size — Klasa
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_variable_size
- allocators/stdext::max_variable_size::allocated
- allocators/stdext::max_variable_size::deallocated
- allocators/stdext::max_variable_size::full
- allocators/stdext::max_variable_size::released
- allocators/stdext::max_variable_size::saved
helpviewer_keywords:
- stdext::max_variable_size
- stdext::max_variable_size [C++], allocated
- stdext::max_variable_size [C++], deallocated
- stdext::max_variable_size [C++], full
- stdext::max_variable_size [C++], released
- stdext::max_variable_size [C++], saved
ms.assetid: 9f2e9df0-4148-4b37-bc30-f8eca0ef86ae
ms.openlocfilehash: 79e37d8c464a009e4a5196aeacc8d4a718e355b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370972"
---
# <a name="max_variable_size-class"></a>max_variable_size — Klasa

Opisuje [obiekt klasy max,](../standard-library/allocators-header.md) który ogranicza [obiekt freelist](../standard-library/freelist-class.md) do maksymalnej długości, która jest w przybliżeniu proporcjonalna do liczby przydzielonych bloków pamięci.

## <a name="syntax"></a>Składnia

```cpp
class max_variable_size
```

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[max_variable_size](#max_variable_size)|Konstruuje obiekt `max_variable_size`typu .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[Przydzielone](#allocated)|Zwiększa liczbę przydzielonych bloków pamięci.|
|[Dealokowane](#deallocated)|Zmniejsza liczbę przydzielonych bloków pamięci.|
|[Pełne](#full)|Zwraca wartość, która określa, czy więcej bloków pamięci powinny zostać dodane do listy wolnych.|
|[Wydany](#released)|Zmniejsza liczbę bloków pamięci na liście wolnych.|
|[Zapisano](#saved)|Zwiększa liczbę bloków pamięci na liście wolnych.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<alokatory>

**Obszar nazw:** stdext

## <a name="max_variable_sizeallocated"></a><a name="allocated"></a>max_variable_size::przydzielone

Zwiększa liczbę przydzielonych bloków pamięci.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*_Nx*|Wartość przyrostu.|

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego dodaje *_Nx* `_Nallocs`do zapisanej wartości . Ta funkcja elementu członkowskiego jest `cache_freelist::allocate` wywoływana po każdym pomyślnym wywołaniu przez operatora **nowego**. Argument *_Nx* jest liczba bloków pamięci w fragmencie przydzielonym przez operatora **new**.

## <a name="max_variable_sizedeallocated"></a><a name="deallocated"></a>max_variable_size::dlokowane

Zmniejsza liczbę przydzielonych bloków pamięci.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*_Nx*|Wartość przyrostu.|

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego odejmuje *_Nx* od `_Nallocs`zapisanej wartości . Ta funkcja elementu członkowskiego jest `cache_freelist::deallocate` wywoływana po każdym wywołaniu przez operatora **delete**. Argument *_Nx* jest liczba bloków pamięci w fragmencie cofnięte przez operatora **usunąć**.

## <a name="max_variable_sizefull"></a><a name="full"></a>max_variable_size::pełna

Zwraca wartość, która określa, czy więcej bloków pamięci powinny zostać dodane do listy wolnych.

```cpp
bool full();
```

### <a name="return-value"></a>Wartość zwracana

**prawda,** jeśli `_Nallocs / 16 + 16 <= _Nblocks`.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu `cache_freelist::deallocate`członkowskiego jest wywoływana przez . Jeśli wywołanie **true**zwraca `deallocate` true , umieszcza blok pamięci na liście wolnych; jeśli zwraca false, `deallocate` wywołuje delete operatora, aby zdyskontować blok. **delete**

## <a name="max_variable_sizemax_variable_size"></a><a name="max_variable_size"></a>max_variable_size::max_variable_size

Konstruuje obiekt `max_variable_size`typu .

```cpp
max_variable_size();
```

### <a name="remarks"></a>Uwagi

Konstruktor inicjuje `_Nblocks` przechowywane `_Nallocs` wartości i do zera.

## <a name="max_variable_sizereleased"></a><a name="released"></a>max_variable_size::zwolniony

Zmniejsza liczbę bloków pamięci na liście wolnych.

```cpp
void released();
```

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego zmniejsza `_Nblocks`wartość zapisaną . Funkcja `released` elementu członkowskiego bieżącej klasy `cache_freelist::allocate` max jest wywoływana za każdym razem, gdy usuwa blok pamięci z listy wolnych.

## <a name="max_variable_sizesaved"></a><a name="saved"></a>max_variable_size::zapisane

Zwiększa liczbę bloków pamięci na liście wolnych.

```cpp
void saved();
```

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego zwiększa `_Nblocks`wartość zapisaną . Ta funkcja elementu `cache_freelist::deallocate` członkowskiego jest wywoływana przez każdym razem, gdy umieszcza blok pamięci na liście wolnych.

## <a name="see-also"></a>Zobacz też

[\<>alokatorów](../standard-library/allocators-header.md)
