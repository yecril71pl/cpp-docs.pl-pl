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
ms.openlocfilehash: 507d35179b9fa86399e56b18171800f41eaf1f10
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371487"
---
# <a name="factorycache-structure"></a>FactoryCache — Struktura

Obsługuje infrastrukturę biblioteki szablonów środowiska wykonawczego systemu Windows W++ i nie jest przeznaczona do użycia bezpośrednio z kodu.

## <a name="syntax"></a>Składnia

```cpp
struct FactoryCache;
```

## <a name="remarks"></a>Uwagi

Zawiera lokalizację fabryki klas i wartość identyfikującą zarejestrowany obiekt klasy wrt lub COM.

## <a name="members"></a>Elementy członkowskie

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

Nazwa                              | Opis
--------------------------------- | ------------------------------------------------------------------------------------------------------------------------------
[FactoryCache::plik cookie](#cookie)   | Zawiera wartość identyfikującą zarejestrowany obiekt klasy Środowiska Wykonawczego systemu Windows lub COM, a później używany do wyrejestrowania obiektu.
[FactoryCache::factory](#factory) | Wskazuje fabrykę środowiska wykonawczego systemu Windows lub klasy COM.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`FactoryCache`

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Obszar nazw:** Microsoft::WRL::Dszczegóły

## <a name="factorycachecookie"></a><a name="cookie"></a>FactoryCache::plik cookie

Obsługuje infrastrukturę biblioteki szablonów środowiska wykonawczego systemu Windows W++ i nie jest przeznaczona do użycia bezpośrednio z kodu.

```cpp
union {
   WINRT_REGISTRATION_COOKIE winrt;
   DWORD com;
} cookie;
```

### <a name="remarks"></a>Uwagi

Zawiera wartość identyfikującą zarejestrowany obiekt klasy Środowiska Wykonawczego systemu Windows lub COM, a później używany do wyrejestrowania obiektu.

## <a name="factorycachefactory"></a><a name="factory"></a>FactoryCache::factory

Obsługuje infrastrukturę biblioteki szablonów środowiska wykonawczego systemu Windows W++ i nie jest przeznaczona do użycia bezpośrednio z kodu.

```cpp
IUnknown* factory;
```

### <a name="remarks"></a>Uwagi

Wskazuje fabrykę środowiska wykonawczego systemu Windows lub klasy COM.
