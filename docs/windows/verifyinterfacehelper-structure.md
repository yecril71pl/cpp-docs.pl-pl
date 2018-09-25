---
title: Verifyinterfacehelper — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/24/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::VerifyInterfaceHelper
- implements/Microsoft::WRL::Details::VerifyInterfaceHelper::Verify
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::VerifyInterfaceHelper structure
- Microsoft::WRL::Details::VerifyInterfaceHelper::Verify method
ms.assetid: ea95b641-199a-4fdf-964b-186b40cb3ba7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e7aa7d796fb30a30a100f5f914feec57909407e5
ms.sourcegitcommit: edb46b0239a0e616af4ec58906e12338c3e8d2c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47169765"
---
# <a name="verifyinterfacehelper-structure"></a>VerifyInterfaceHelper — Struktura

Obsługuje infrastrukturę Biblioteka szablonów C++ środowiska wykonawczego Windows i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
template <
   bool isWinRTInterface,
   typename I
>
struct VerifyInterfaceHelper;

template <
   typename I
>
struct VerifyInterfaceHelper<false, I>;
```

### <a name="parameters"></a>Parametry

*I*<br/>
Interfejs, aby sprawdzić.

*isWinRTInterface*

## <a name="remarks"></a>Uwagi

Sprawdza, czy interfejs określony przez parametr szablonu spełnia określone wymagania.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

Nazwa                                            | Opis
----------------------------------------------- | ---------------------------------------------------------------------------------------------------
[VerifyInterfaceHelper::Verify, metoda](#verify) | Sprawdza, czy interfejs określony przez bieżący parametr szablonu spełnia określone wymagania.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`VerifyInterfaceHelper`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::wrl:: details

## <a name="verify"></a>VerifyInterfaceHelper::Verify

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
static void Verify();
```

### <a name="remarks"></a>Uwagi

Sprawdza, czy interfejs określony przez bieżący parametr szablonu spełnia określone wymagania.
