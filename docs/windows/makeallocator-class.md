---
title: Makeallocator — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator
- implements/Microsoft::WRL::Details::MakeAllocator::Allocate
- implements/Microsoft::WRL::Details::MakeAllocator::Detach
- implements/Microsoft::WRL::Details::MakeAllocator::MakeAllocator
- implements/Microsoft::WRL::Details::MakeAllocator::~MakeAllocator
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::MakeAllocator class
- Microsoft::WRL::Details::MakeAllocator::Allocate method
- Microsoft::WRL::Details::MakeAllocator::Detach method
- Microsoft::WRL::Details::MakeAllocator::MakeAllocator, constructor
- Microsoft::WRL::Details::MakeAllocator::~MakeAllocator, destructor
ms.assetid: a1114615-abd7-4a56-9bc3-750c118f0fa1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 93fb92c51ee16593f9314d7172f0b38e6d0918e8
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49162480"
---
# <a name="makeallocator-class"></a>MakeAllocator — Klasa

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

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
**wartość true,** można przydzielić pamięci dla obiektu, który obsługuje słabe odwołania; **false** można przydzielić pamięci dla obiektu, który nie obsługuje słabe odwołania.

## <a name="remarks"></a>Uwagi

Przydziela pamięć dla klasy aktywowalnej, z lub bez niej odwołanie tymczasowe wsparcia.

Zastąp `MakeAllocator` klasę, aby wdrożyć model przydzielania pamięci zdefiniowane przez użytkownika.

`MakeAllocator` Zazwyczaj służy do zapobiec przeciekom pamięci, jeśli obiekt zgłasza wyjątek w trakcie konstruowania.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                                  | Opis
----------------------------------------------------- | ----------------------------------------------------------------
[MakeAllocator::MakeAllocator](#makeallocator)        | Inicjuje nowe wystąpienie klasy `MakeAllocator` klasy.
[MakeAllocator:: ~ MakeAllocator](#tilde-makeallocator) | Deinicjuje bieżące wystąpienie `MakeAllocator` klasy.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                 | Opis
------------------------------------ | -----------------------------------------------------------------------------------------------------------
[MakeAllocator::Allocate](#allocate) | Przydziela pamięć i kojarzy ją z bieżącymi `MakeAllocator` obiektu.
[MakeAllocator::Detach](#detach)     | Powoduje usunięcie pamięci przydzielonej przez [przydziel](#allocate) z bieżącej metody `MakeAllocator` obiektu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`MakeAllocator`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::wrl:: details

## <a name="allocate"></a>MakeAllocator::Allocate

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
__forceinline void* Allocate();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, wskaźnik do przydzielonego pamięci. w przeciwnym razie `nullptr`.

### <a name="remarks"></a>Uwagi

Przydziela pamięć i kojarzy ją z bieżącymi `MakeAllocator` obiektu.

Rozmiar alokacji pamięci jest rozmiar o typie określonym przez bieżącą `MakeAllocator` parametru szablonu.

Deweloper musi zastąpić tylko `Allocate()` metodę, aby wdrożyć model przydzielania pamięci różnych.

## <a name="detach"></a>MakeAllocator::Detach

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
__forceinline void Detach();
```

### <a name="remarks"></a>Uwagi

Powoduje usunięcie pamięci przydzielonej przez [przydziel](#allocate) z bieżącej metody `MakeAllocator` obiektu.

Jeśli wywołasz `Detach()`, jesteś odpowiedzialny za usunięcie pamięci dostarczonej przez `Allocate` metody.

## <a name="makeallocator"></a>MakeAllocator::MakeAllocator

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
MakeAllocator();
```

### <a name="remarks"></a>Uwagi

Inicjuje nowe wystąpienie klasy `MakeAllocator` klasy.

## <a name="tilde-makeallocator"></a>MakeAllocator:: ~ MakeAllocator

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
~MakeAllocator();
```

### <a name="remarks"></a>Uwagi

Deinicjuje bieżące wystąpienie `MakeAllocator` klasy.

Ten destruktor spowoduje również usunięcie podstawowych ilość przydzielonej pamięci w razie potrzeby.
