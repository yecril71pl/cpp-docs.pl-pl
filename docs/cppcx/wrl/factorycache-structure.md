---
title: FactoryCache — Struktura
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::FactoryCache
- module/Microsoft::WRL::Details::FactoryCache::cookie
- module/Microsoft::WRL::Details::FactoryCache::factory
helpviewer_keywords:
- Microsoft::WRL::Details::FactoryCache structure
- Microsoft::WRL::Details::FactoryCache::cookie data member
- Microsoft::WRL::Details::FactoryCache::factory data member
ms.assetid: 624544e6-0989-47f6-a3e9-edb60e1ee6d4
ms.openlocfilehash: 7196363567dffa43844bbbd1de76934a317302d1
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58787428"
---
# <a name="factorycache-structure"></a>FactoryCache — Struktura

Obsługuje infrastrukturę Biblioteka szablonów C++ środowiska wykonawczego Windows i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
struct FactoryCache;
```

## <a name="remarks"></a>Uwagi

Zawiera lokalizację fabryki klas i wartość, która identyfikuje zarejestrowany wrt lub obiekt klasy COM.

## <a name="members"></a>Elementy członkowskie

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

Nazwa                              | Opis
--------------------------------- | ------------------------------------------------------------------------------------------------------------------------------
[FactoryCache::cookie](#cookie)   | Zawiera wartość, która identyfikuje zarejestrowanych obiektu klasy środowiska wykonawczego Windows lub COM i jest później używany do wyrejestrowania obiektu.
[FactoryCache::factory](#factory) | Wskazuje fabrykę klas Windows Runtime lub COM.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`FactoryCache`

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::WRL::Details

## <a name="cookie"></a>FactoryCache::cookie

Obsługuje infrastrukturę Biblioteka szablonów C++ środowiska wykonawczego Windows i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
union {
   WINRT_REGISTRATION_COOKIE winrt;
   DWORD com;
} cookie;
```

### <a name="remarks"></a>Uwagi

Zawiera wartość, która identyfikuje zarejestrowanych obiektu klasy środowiska wykonawczego Windows lub COM i jest później używany do wyrejestrowania obiektu.

## <a name="factory"></a>FactoryCache::factory

Obsługuje infrastrukturę Biblioteka szablonów C++ środowiska wykonawczego Windows i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
IUnknown* factory;
```

### <a name="remarks"></a>Uwagi

Wskazuje fabrykę klas Windows Runtime lub COM.