---
title: AsyncBase::CheckValidStateForResultsCall, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::CheckValidStateForResultsCall
dev_langs:
- C++
helpviewer_keywords:
- CheckValidStateForResultsCall method
ms.assetid: 87ca6805-bff1-4063-b855-6dd26132deff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 398f46d5f8eb15d961d80b9a7a20b758fffd09c3
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42584239"
---
# <a name="asyncbasecheckvalidstateforresultscall-method"></a>AsyncBase::CheckValidStateForResultsCall — Metoda

Sprawdza, czy wyniki operacji asynchronicznej może być zbierana w bieżącym stanie asynchronicznego.

## <a name="syntax"></a>Składnia

```cpp
inline HRESULT CheckValidStateForResultsCall();
```

## <a name="return-value"></a>Wartość zwracana

S_OK, jeśli wyniki mogą być zbierane; w przeciwnym razie E_ILLEGAL_METHOD_CALLE_ILLEGAL_METHOD_CALL.

## <a name="requirements"></a>Wymagania

**Nagłówek:** async.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[AsyncBase, klasa](../windows/asyncbase-class.md)