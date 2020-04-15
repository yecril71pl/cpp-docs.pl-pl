---
title: max_fixed_size — Klasa
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_fixed_size
- allocators/stdext::max_fixed_size::allocated
- allocators/stdext::max_fixed_size::deallocated
- allocators/stdext::max_fixed_size::full
- allocators/stdext::max_fixed_size::released
- allocators/stdext::max_fixed_size::saved
helpviewer_keywords:
- stdext::max_fixed_size
- stdext::max_fixed_size [C++], allocated
- stdext::max_fixed_size [C++], deallocated
- stdext::max_fixed_size [C++], full
- stdext::max_fixed_size [C++], released
- stdext::max_fixed_size [C++], saved
ms.assetid: 8c8f4588-37e9-4579-8168-ba3553800914
ms.openlocfilehash: 7f75dd71caa3cfcfec19264b1da62c6d47a3e01d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371003"
---
# <a name="max_fixed_size-class"></a>max_fixed_size — Klasa

Opisuje [obiekt klasy max,](../standard-library/allocators-header.md) który ogranicza [obiekt freelist](../standard-library/freelist-class.md) do stałej maksymalnej długości.

## <a name="syntax"></a>Składnia

```cpp
template <std::size_t Max>
class max_fixed_size
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Max*|Max klasa, która określa maksymalną liczbę elementów do przechowywania w `freelist`.|

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[max_fixed_size](#max_fixed_size)|Konstruuje obiekt `max_fixed_size`typu .|

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

## <a name="max_fixed_sizeallocated"></a><a name="allocated"></a>max_fixed_size::przydzielone

Zwiększa liczbę przydzielonych bloków pamięci.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*_Nx*|Wartość przyrostu.|

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego nic nie robi. Ta funkcja elementu członkowskiego jest `cache_freelist::allocate` wywoływana po każdym pomyślnym wywołaniu przez operatora **nowego**. Argument *_Nx* jest liczba bloków pamięci w fragmencie przydzielonym przez operatora **new**.

## <a name="max_fixed_sizedeallocated"></a><a name="deallocated"></a>max_fixed_size::dlokowane

Zmniejsza liczbę przydzielonych bloków pamięci.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*_Nx*|Wartość przyrostu.|

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego nic nie robi. Ta funkcja elementu członkowskiego jest `cache_freelist::deallocate` wywoływana po każdym wywołaniu przez operatora **delete**. Argument *_Nx* jest liczba bloków pamięci w fragmencie cofnięte przez operatora **usunąć**.

## <a name="max_fixed_sizefull"></a><a name="full"></a>max_fixed_size::pełna

Zwraca wartość, która określa, czy więcej bloków pamięci powinny zostać dodane do listy wolnych.

```cpp
bool full();
```

### <a name="return-value"></a>Wartość zwracana

**prawda,** jeśli `Max <= _Nblocks`; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu `cache_freelist::deallocate`członkowskiego jest wywoływana przez . Jeśli wywołanie **true**zwraca `deallocate` true , umieszcza blok pamięci na liście wolnych; jeśli zwraca false, `deallocate` wywołuje delete operatora, aby zdyskontować blok. **delete**

## <a name="max_fixed_sizemax_fixed_size"></a><a name="max_fixed_size"></a>max_fixed_size::max_fixed_size

Konstruuje obiekt `max_fixed_size`typu .

```cpp
max_fixed_size();
```

### <a name="remarks"></a>Uwagi

Ten konstruktor inicjuje wartość `_Nblocks` przechowywaną do zera.

## <a name="max_fixed_sizereleased"></a><a name="released"></a>max_fixed_size::zwolniony

Zmniejsza liczbę bloków pamięci na liście wolnych.

```cpp
void released();
```

### <a name="remarks"></a>Uwagi

Zmniejsza wartość zapisaną `_Nblocks`. Funkcja `released` elementu członkowskiego bieżącej [klasy](../standard-library/allocators-header.md) `cache_freelist::allocate` max jest wywoływana za każdym razem, gdy usuwa blok pamięci z listy wolnych.

## <a name="max_fixed_sizesaved"></a><a name="saved"></a>max_fixed_size::zapisane

Zwiększa liczbę bloków pamięci na liście wolnych.

```cpp
void saved();
```

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego zwiększa `_Nblocks`wartość zapisaną . Ta funkcja elementu `cache_freelist::deallocate` członkowskiego jest wywoływana przez każdym razem, gdy umieszcza blok pamięci na liście wolnych.

## <a name="see-also"></a>Zobacz też

[\<>alokatorów](../standard-library/allocators-header.md)
