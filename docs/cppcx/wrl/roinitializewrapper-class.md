---
title: RoInitializeWrapper — Klasa
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::HRESULT
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::RoInitializeWrapper
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::~RoInitializeWrapper
helpviewer_keywords:
- Microsoft::WRL::Wrappers::RoInitializeWrapper class
- Microsoft::WRL::Wrappers::RoInitializeWrapper::operator HRESULT operator
- Microsoft::WRL::Wrappers::RoInitializeWrapper::RoInitializeWrapper, constructor
- Microsoft::WRL::Wrappers::RoInitializeWrapper::~RoInitializeWrapper, destructor
ms.assetid: 4055fbe0-63a7-4c06-b5a0-414fda5640e5
ms.openlocfilehash: eba9162f17b98d13a9caf956b4f110b89dd81c37
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371220"
---
# <a name="roinitializewrapper-class"></a>RoInitializeWrapper — Klasa

Inicjuje środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```cpp
class RoInitializeWrapper;
```

## <a name="remarks"></a>Uwagi

`RoInitializeWrapper`jest wygoda, która inicjuje środowiska wykonawczego systemu Windows i zwraca HRESULT, który wskazuje, czy operacja zakończyła się pomyślnie. Ponieważ wywołania `::Windows::Foundation::Uninitialize`destruktora klasy, wystąpienia `RoInitializeWrapper` muszą być zadeklarowane w zakresie globalnym lub najwyższym poziomie.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                                                    | Opis
----------------------------------------------------------------------- | -----------------------------------------------------------------
[RoInitializeWrapper::RoInitializeWrapper](#roinitializewrapper)        | Inicjuje nowe wystąpienie klasy `RoInitializeWrapper`.
[RoInitializeWrapper::~RoInitializeWrapper](#tilde-roinitializewrapper) | Niszczy bieżące wystąpienie `RoInitializeWrapper` klasy.

### <a name="public-operators"></a>Operatory publiczne

Nazwa                                       | Opis
------------------------------------------ | ------------------------------------------------------------------------
[RoInitializeWrapper::HRESULT()](#hresult) | Pobiera HRESULT produkowane przez `RoInitializeWrapper` konstruktora.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`RoInitializeWrapper`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Obszar nazw:** Microsoft::WRL::Otoki

## <a name="roinitializewrapperhresult"></a><a name="hresult"></a>RoInitializeWrapper::HRESULT()

Pobiera wartość HRESULT produkowane przez `RoInitializeWrapper` ostatni konstruktora.

```cpp
operator HRESULT()
```

## <a name="roinitializewrapperroinitializewrapper"></a><a name="roinitializewrapper"></a>RoInitializeWrapper::RoInitializeWrapper

Inicjuje nowe wystąpienie klasy `RoInitializeWrapper`.

```cpp
RoInitializeWrapper(RO_INIT_TYPE flags)
```

### <a name="parameters"></a>Parametry

*flagi*<br/>
Jednym z wyliczeń RO_INIT_TYPE, który określa obsługę zapewnianą przez środowisko wykonawcze systemu Windows.

### <a name="remarks"></a>Uwagi

Klasa `RoInitializeWrapper` wywołuje `Windows::Foundation::Initialize(flags)`.

## <a name="roinitializewrapperroinitializewrapper"></a><a name="tilde-roinitializewrapper"></a>RoInitializeWrapper::~RoInitializeWrapper

Uninitializes środowiska wykonawczego systemu Windows.

```cpp
~RoInitializeWrapper()
```

### <a name="remarks"></a>Uwagi

Klasa `RoInitializeWrapper` wywołuje `Windows::Foundation::Uninitialize()`.
