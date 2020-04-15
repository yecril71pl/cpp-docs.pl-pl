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
ms.openlocfilehash: dc0d83f2550646572a4eff2bec7850037c6dbf6a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371332"
---
# <a name="makeallocator-class"></a>MakeAllocator — Klasa

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

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
**true,** aby przydzielić pamięć dla obiektu, który obsługuje słabe odwołania; **false,** aby przydzielić pamięć dla obiektu, który nie obsługuje słabych odwołań.

## <a name="remarks"></a>Uwagi

Przydziela pamięć dla klasy aktywacji, z lub bez wsparcia odniesienia słabe.

Zastądnie klasy, `MakeAllocator` aby zaimplementować model alokacji pamięci zdefiniowanej przez użytkownika.

`MakeAllocator`jest zwykle używany, aby zapobiec przeciekom pamięci, jeśli obiekt zostanie rzuci podczas budowy.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                                  | Opis
----------------------------------------------------- | ----------------------------------------------------------------
[MakeAllocator::MakeAllocator](#makeallocator)        | Inicjuje nowe wystąpienie klasy `MakeAllocator`.
[MakeAllocator::~MakeAllocator](#tilde-makeallocator) | Deinitializes bieżące wystąpienie `MakeAllocator` klasy.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                 | Opis
------------------------------------ | -----------------------------------------------------------------------------------------------------------
[MakeAllocator::Przydziel](#allocate) | Przydziela pamięć i kojarzy ją `MakeAllocator` z bieżącym obiektem.
[MakeAllocator::Detach](#detach)     | Disassociates pamięci przydzielone przez [Allocate](#allocate) metody z bieżącego `MakeAllocator` obiektu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`MakeAllocator`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Obszar nazw:** Microsoft::WRL::Dszczegóły

## <a name="makeallocatorallocate"></a><a name="allocate"></a>MakeAllocator::Przydziel

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
__forceinline void* Allocate();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, wskaźnik do przydzielonej pamięci; w `nullptr`przeciwnym razie , .

### <a name="remarks"></a>Uwagi

Przydziela pamięć i kojarzy ją `MakeAllocator` z bieżącym obiektem.

Rozmiar przydzielonej pamięci jest rozmiarem typu określonego `MakeAllocator` przez bieżący parametr szablonu.

Deweloper musi zastąpić tylko metodę, `Allocate()` aby zaimplementować inny model alokacji pamięci.

## <a name="makeallocatordetach"></a><a name="detach"></a>MakeAllocator::Detach

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
__forceinline void Detach();
```

### <a name="remarks"></a>Uwagi

Disassociates pamięci przydzielone przez [Allocate](#allocate) metody z bieżącego `MakeAllocator` obiektu.

Jeśli wywołasz, `Detach()`jesteś odpowiedzialny za usunięcie pamięci `Allocate` dostarczonej przez metodę.

## <a name="makeallocatormakeallocator"></a><a name="makeallocator"></a>MakeAllocator::MakeAllocator

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
MakeAllocator();
```

### <a name="remarks"></a>Uwagi

Inicjuje nowe wystąpienie klasy `MakeAllocator`.

## <a name="makeallocatormakeallocator"></a><a name="tilde-makeallocator"></a>MakeAllocator::~MakeAllocator

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
~MakeAllocator();
```

### <a name="remarks"></a>Uwagi

Deinitializes bieżące wystąpienie `MakeAllocator` klasy.

Ten destruktor usuwa również podstawowej przydzielonej pamięci, jeśli to konieczne.
