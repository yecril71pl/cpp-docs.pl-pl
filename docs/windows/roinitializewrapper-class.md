---
title: RoInitializeWrapper, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::HRESULT
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::RoInitializeWrapper
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::~RoInitializeWrapper
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::RoInitializeWrapper class
- Microsoft::WRL::Wrappers::RoInitializeWrapper::operator HRESULT operator
- Microsoft::WRL::Wrappers::RoInitializeWrapper::RoInitializeWrapper, constructor
- Microsoft::WRL::Wrappers::RoInitializeWrapper::~RoInitializeWrapper, destructor
ms.assetid: 4055fbe0-63a7-4c06-b5a0-414fda5640e5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3dd1b5df8749f22873a52782b6f528760c3823a1
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48788764"
---
# <a name="roinitializewrapper-class"></a>RoInitializeWrapper — Klasa

Inicjuje środowisko wykonawcze Windows.

## <a name="syntax"></a>Składnia

```cpp
class RoInitializeWrapper;
```

## <a name="remarks"></a>Uwagi

`RoInitializeWrapper` To udogodnienie inicjuje środowiska wykonawczego Windows, która zwraca wartość HRESULT, która wskazuje, czy operacja zakończyła się powodzeniem. Ponieważ wywołuje destruktor klasy `::Windows::Foundation::Uninitialize`, wystąpień `RoInitializeWrapper` musi być zadeklarowana w zakresie globalnym lub najwyższego poziomu.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                                                    | Opis
----------------------------------------------------------------------- | -----------------------------------------------------------------
[RoInitializeWrapper::RoInitializeWrapper](#roinitializewrapper)        | Inicjuje nowe wystąpienie klasy `RoInitializeWrapper` klasy.
[RoInitializeWrapper:: ~ RoInitializeWrapper](#tilde-roinitializewrapper) | Likwiduje bieżące wystąpienie `RoInitializeWrapper` klasy.

### <a name="public-operators"></a>Operatory publiczne

Nazwa                                       | Opis
------------------------------------------ | ------------------------------------------------------------------------
[Roinitializewrapper:: HRESULT()](#hresult) | Pobiera wartość HRESULT produkowane przez `RoInitializeWrapper` konstruktora.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`RoInitializeWrapper`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="hresult"></a>Roinitializewrapper:: HRESULT()

Pobiera wartość HRESULT produkowane przez ostatnią `RoInitializeWrapper` konstruktora.

```cpp
operator HRESULT()  
```

## <a name="roinitializewrapper"></a>RoInitializeWrapper::RoInitializeWrapper

Inicjuje nowe wystąpienie klasy `RoInitializeWrapper` klasy.

```cpp
RoInitializeWrapper(   RO_INIT_TYPE flags)  
```

### <a name="parameters"></a>Parametry

*flagi*<br/>
Jedno z wyliczeń RO_INIT_TYPE, które określa pomoc techniczną świadczoną przez środowisko wykonawcze Windows.

### <a name="remarks"></a>Uwagi

`RoInitializeWrapper` Wywołuje klasę `Windows::Foundation::Initialize(flags)`.

## <a name="tilde-roinitializewrapper"></a>RoInitializeWrapper:: ~ RoInitializeWrapper

Deinicjuje środowiska wykonawczego Windows.

```cpp
~RoInitializeWrapper()  
```

### <a name="remarks"></a>Uwagi

`RoInitializeWrapper` Wywołuje klasę `Windows::Foundation::Uninitialize()`.
