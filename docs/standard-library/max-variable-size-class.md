---
title: max_variable_size — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::max_variable_size
- allocators/stdext::max_variable_size::allocated
- allocators/stdext::max_variable_size::deallocated
- allocators/stdext::max_variable_size::full
- allocators/stdext::max_variable_size::released
- allocators/stdext::max_variable_size::saved
dev_langs:
- C++
helpviewer_keywords:
- stdext::max_variable_size
- stdext::max_variable_size [C++], allocated
- stdext::max_variable_size [C++], deallocated
- stdext::max_variable_size [C++], full
- stdext::max_variable_size [C++], released
- stdext::max_variable_size [C++], saved
ms.assetid: 9f2e9df0-4148-4b37-bc30-f8eca0ef86ae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 974cee757708b9f7b1e48ea3bec3c4af98ced558
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957658"
---
# <a name="maxvariablesize-class"></a>max_variable_size — Klasa

W tym artykule opisano [maksymalnej liczby klas](../standard-library/allocators-header.md) obiekt, który ogranicza [FreeList —](../standard-library/freelist-class.md) obiektu do maksymalnej długości, który jest około proporcjonalny do liczby przydzielonych bloków pamięci.

## <a name="syntax"></a>Składnia

```cpp
class max_variable_size
```

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[max_variable_size —](#max_variable_size)|Tworzy obiekt typu `max_variable_size`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[przydzielona](#allocated)|Zwiększa liczbę bloków ilość przydzielonej pamięci.|
|[Cofnięto alokację](#deallocated)|Dekrementuje liczbę przydzielonych bloków pamięci.|
|[full](#full)|Zwraca wartość określającą, czy więcej bloków pamięci powinna być dodana do listy bezpłatne.|
|[Wydana](#released)|Zmniejsza liczbę pamięci blokuje się na liście bezpłatne.|
|[zapisano](#saved)|Zwiększa liczbę bloków pamięci na liście bezpłatne.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<buforów >

**Namespace:** stdext

## <a name="allocated"></a>  max_variable_size::allocated

Zwiększa liczbę bloków ilość przydzielonej pamięci.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*_Nx*|Wartość przyrostu.|

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego dodaje *_Nx* do wartości przechowywanej `_Nallocs`. Ta funkcja członkowska jest wywoływana po każdym pomyślnym wywołaniem przez `cache_freelist::allocate` operatora **nowe**. Argument *_Nx* jest to liczba bloków pamięci we fragmencie przydzielonej przez operator **nowe**.

## <a name="deallocated"></a>  max_variable_size::deallocated

Dekrementuje liczbę przydzielonych bloków pamięci.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*_Nx*|Wartość przyrostu.|

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego odejmuje *_Nx* z wartości przechowywanej `_Nallocs`. Ta funkcja członkowska jest wywoływana po każdym wywołaniu przez `cache_freelist::deallocate` operatora **Usuń**. Argument *_Nx* jest to liczba bloków pamięci we fragmencie cofnięta przez operator **Usuń**.

## <a name="full"></a>  max_variable_size::Full

Zwraca wartość określającą, czy więcej bloków pamięci powinna być dodana do listy bezpłatne.

```cpp
bool full();
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli `_Nallocs / 16 + 16 <= _Nblocks`.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana przez `cache_freelist::deallocate`. Jeśli to wywołanie zwraca **true**, `deallocate` umieszcza blok pamięci na liście bezpłatne; Jeśli zostanie zwrócona wartość false, `deallocate` operatora wywołania **Usuń** można cofnąć alokacji bloku.

## <a name="max_variable_size"></a>  max_variable_size::max_variable_size

Tworzy obiekt typu `max_variable_size`.

```cpp
max_variable_size();
```

### <a name="remarks"></a>Uwagi

Konstruktor inicjuje przechowywane wartości `_Nblocks` i `_Nallocs` do zera.

## <a name="released"></a>  max_variable_size::released

Zmniejsza liczbę pamięci blokuje się na liście bezpłatne.

```cpp
void released();
```

### <a name="remarks"></a>Uwagi

Ten element członkowski funkcji Dekrementuje przechowywaną wartość `_Nblocks`. `released` Funkcji składowej klasy bieżący maksymalny jest wywoływana przez `cache_freelist::allocate` zawsze, gdy usunie blok pamięci z bezpłatnych listy.

## <a name="saved"></a>  max_variable_size::Saved

Zwiększa liczbę bloków pamięci na liście bezpłatne.

```cpp
void saved();
```

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego zwiększa przechowywaną wartość `_Nblocks`. Ta funkcja członkowska jest wywoływana przez `cache_freelist::deallocate` zawsze umieszcza blok pamięci na liście bezpłatne.

## <a name="see-also"></a>Zobacz także

[\<allocators — >](../standard-library/allocators-header.md)<br/>
