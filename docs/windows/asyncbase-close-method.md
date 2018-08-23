---
title: AsyncBase::Close, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: a52b1124-754b-4393-b491-64aae0c22f1c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 732eb6f8668f7742e23e1ea410dcc659bc3d36c7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605349"
---
# <a name="asyncbaseclose-method"></a>AsyncBase::Close — Metoda

Zamyka operację asynchroniczną.

## <a name="syntax"></a>Składnia

```cpp
STDMETHOD(
   Close
)(void) override;
```

## <a name="return-value"></a>Wartość zwracana

S_OK, jeśli operacja zostanie zamknięty lub już zamknięte; w przeciwnym razie E_ILLEGAL_STATE_CHANGE.

## <a name="remarks"></a>Uwagi

**Close()** jest domyślna Implementacja klasy `IAsyncInfo::Close`, a nie rzeczywiste działa. Aby rzeczywiście zamknąć operację asynchroniczną, należy zastąpić `OnClose()` czystej wirtualnej metody.

## <a name="requirements"></a>Wymagania

**Nagłówek:** async.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[AsyncBase, klasa](../windows/asyncbase-class.md)