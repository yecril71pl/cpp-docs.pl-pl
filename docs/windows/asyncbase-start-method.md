---
title: AsyncBase::Start, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::Start
dev_langs:
- C++
helpviewer_keywords:
- Start method
ms.assetid: 67405c9d-0d1a-4c1e-8ea4-6ba01c1f90d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d81a3f29e99f49b03eb76f44af60c42d433e0bdc
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42611235"
---
# <a name="asyncbasestart-method"></a>AsyncBase::Start — Metoda

Rozpoczyna operację asynchroniczną.

## <a name="syntax"></a>Składnia

```cpp
STDMETHOD(
   Start
)(void);
```

## <a name="return-value"></a>Wartość zwracana

S_OK, jeśli operacja rozpoczyna się lub jest już uruchomiona; w przeciwnym razie E_ILLEGAL_STATE_CHANGE.

## <a name="remarks"></a>Uwagi

**Start()** jest domyślna Implementacja klasy `IAsyncInfo::Start`, a nie rzeczywiste działa. Uruchamia operację asynchroniczną, należy zastąpić `OnStart()` czystej wirtualnej metody.

## <a name="requirements"></a>Wymagania

**Nagłówek:** async.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[AsyncBase, klasa](../windows/asyncbase-class.md)