---
title: HandleT::Detach, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method
ms.assetid: f7df0f90-fafb-4d1b-a215-a6c62941f6b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7b66d5c65dd084da564067cd62242b315f6da182
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42591377"
---
# <a name="handletdetach-method"></a>HandleT::Detach — Metoda

Powoduje usunięcie bieżącego **HandleT** obiekt z jego podstawowego dojścia.

## <a name="syntax"></a>Składnia

```cpp
typename HandleTraits::Type Detach();
```

## <a name="return-value"></a>Wartość zwracana

Podstawowego dojścia.

## <a name="remarks"></a>Uwagi

Po zakończeniu tej operacji, bieżący **HandleT** ustawiono nieprawidłowy stan.

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="see-also"></a>Zobacz też

[HandleT, klasa](../windows/handlet-class.md)