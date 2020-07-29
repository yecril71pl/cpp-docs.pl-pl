---
title: MakeAllocator — Klasa
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator
- implements/Microsoft::WRL::Details::MakeAllocator::Allocate
- implements/Microsoft::WRL::Details::MakeAllocator::Detach
- implements/Microsoft::WRL::Details::MakeAllocator::MakeAllocator
- implements/Microsoft::WRL::Details::MakeAllocator::~MakeAllocator
helpviewer_keywords:
- Microsoft::WRL::Details::MakeAllocator class
- Microsoft::WRL::Details::MakeAllocator::Allocate method
- Microsoft::WRL::Details::MakeAllocator::Detach method
- Microsoft::WRL::Details::MakeAllocator::MakeAllocator, constructor
- Microsoft::WRL::Details::MakeAllocator::~MakeAllocator, destructor
ms.assetid: a1114615-abd7-4a56-9bc3-750c118f0fa1
ms.openlocfilehash: 19d3ab294df8adc059424c97e5733ae9ebb75c9c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218380"
---
# <a name="makeallocator-class"></a>MakeAllocator — Klasa

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
template<
    typename T,
    bool hasWeakReferenceSupport =
          !__is_base_of(RuntimeClassFlags<InhibitWeakReference>,
                        T)
>
class MakeAllocator;

template<typename T>
class MakeAllocator<T, false>;

template<typename T>
class MakeAllocator<T, true>;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Nazwa typu.

*hasWeakReferenceSupport*<br/>
**`true`** Aby przydzielić pamięć dla obiektu, który obsługuje słabe odwołania; **`false`** Aby przydzielić pamięć dla obiektu, który nie obsługuje słabych odwołań.

## <a name="remarks"></a>Uwagi

Przydziela pamięć dla klasy aktywowalnej z niesłabym wsparciem referencyjnym lub bez niego.

Zastąp `MakeAllocator` klasę, aby zaimplementować zdefiniowany przez użytkownika model alokacji pamięci.

`MakeAllocator`jest zwykle używany, aby zapobiec przeciekom pamięci, jeśli obiekt zgłasza podczas konstruowania.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                                  | Opis
----------------------------------------------------- | ----------------------------------------------------------------
[MakeAllocator:: MakeAllocator](#makeallocator)        | Inicjuje nowe wystąpienie klasy `MakeAllocator`.
[MakeAllocator:: ~ MakeAllocator](#tilde-makeallocator) | Deinicjalizuje bieżące wystąpienie `MakeAllocator` klasy.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                 | Opis
------------------------------------ | -----------------------------------------------------------------------------------------------------------
[MakeAllocator:: Allocate](#allocate) | Przydziela pamięć i kojarzy ją z bieżącym `MakeAllocator` obiektem.
[MakeAllocator::D etach](#detach)     | Usuwa pamięć przydzieloną przez metodę [ALLOCATE](#allocate) z bieżącego `MakeAllocator` obiektu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`MakeAllocator`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implementuje. h

**Przestrzeń nazw:** Microsoft:: WRL::D etails

## <a name="makeallocatorallocate"></a><a name="allocate"></a>MakeAllocator:: Allocate

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
__forceinline void* Allocate();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli powiedzie się, wskaźnik do przydzieloną pamięć; w przeciwnym razie **`nullptr`** .

### <a name="remarks"></a>Uwagi

Przydziela pamięć i kojarzy ją z bieżącym `MakeAllocator` obiektem.

Rozmiar przydzielonej pamięci jest rozmiarem typu określonego przez bieżący `MakeAllocator` parametr szablonu.

Deweloper musi zastąpić tylko `Allocate()` metodę, aby zaimplementować inny model alokacji pamięci.

## <a name="makeallocatordetach"></a><a name="detach"></a>MakeAllocator::D etach

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
__forceinline void Detach();
```

### <a name="remarks"></a>Uwagi

Usuwa pamięć przydzieloną przez metodę [ALLOCATE](#allocate) z bieżącego `MakeAllocator` obiektu.

W przypadku wywołania usługi `Detach()` użytkownik jest odpowiedzialny za usunięcie pamięci dostarczonej przez `Allocate` metodę.

## <a name="makeallocatormakeallocator"></a><a name="makeallocator"></a>MakeAllocator:: MakeAllocator

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
MakeAllocator();
```

### <a name="remarks"></a>Uwagi

Inicjuje nowe wystąpienie klasy `MakeAllocator`.

## <a name="makeallocatormakeallocator"></a><a name="tilde-makeallocator"></a>MakeAllocator:: ~ MakeAllocator

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
~MakeAllocator();
```

### <a name="remarks"></a>Uwagi

Deinicjalizuje bieżące wystąpienie `MakeAllocator` klasy.

Ten destruktor usuwa również w razie potrzeby podstawową przydzieloną pamięć.
