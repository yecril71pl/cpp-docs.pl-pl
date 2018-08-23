---
title: Makeallocator — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator
dev_langs:
- C++
helpviewer_keywords:
- MakeAllocator class
ms.assetid: a1114615-abd7-4a56-9bc3-750c118f0fa1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e27be8eaddfc22474f15d7f9358050273252bf8a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42610327"
---
# <a name="makeallocator-class"></a>MakeAllocator — Klasa

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
template<
   typename T,
   bool hasWeakReferenceSupport =
         !__is_base_of(RuntimeClassFlags<InhibitWeakReference>, T)>
 class MakeAllocator;

template<typename T>
class MakeAllocator<T, false>;

template<typename T>
class MakeAllocator<T, true>;
```

### <a name="parameters"></a>Parametry

*T*  
Nazwa typu.

*hasWeakReferenceSupport*  
**wartość true,** można przydzielić pamięci dla obiektu, który obsługuje słabe odwołania; **false** można przydzielić pamięci dla obiektu, który nie obsługuje słabe odwołania.

## <a name="remarks"></a>Uwagi

Przydziela pamięć dla klasy aktywowalnej, z lub bez niej odwołanie tymczasowe wsparcia.

Zastąp **MakeAllocator** klasę, aby wdrożyć model przydzielania pamięci zdefiniowane przez użytkownika.

**MakeAllocator** jest zazwyczaj używany do zapobiec przeciekom pamięci, jeśli obiekt zgłasza wyjątek w trakcie konstruowania.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[MakeAllocator::MakeAllocator, konstruktor](../windows/makeallocator-makeallocator-constructor.md)|Inicjuje nowe wystąpienie klasy **MakeAllocator** klasy.|
|[MakeAllocator::~MakeAllocator, destruktor](../windows/makeallocator-tilde-makeallocator-destructor.md)|Deinicjuje bieżące wystąpienie **MakeAllocator** klasy.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[MakeAllocator::Allocate, metoda](../windows/makeallocator-allocate-method.md)|Przydziela pamięć i kojarzy ją z bieżącymi **MakeAllocator** obiektu.|
|[MakeAllocator::Detach, metoda](../windows/makeallocator-detach-method.md)|Powoduje usunięcie pamięci przydzielonej przez [przydziel](../windows/makeallocator-allocate-method.md) metody z bieżącego **MakeAllocator** obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`MakeAllocator`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::wrl:: details

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)