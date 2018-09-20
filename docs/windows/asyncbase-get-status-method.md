---
title: AsyncBase::get_Status, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::get_Status
dev_langs:
- C++
helpviewer_keywords:
- get_Status method
ms.assetid: 9823ecb9-212e-471d-b76f-7b8f21208905
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c1bb13773736104354d6276fef0a731aa72f22d2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431247"
---
# <a name="asyncbasegetstatus-method"></a>AsyncBase::get_Status — Metoda

Pobiera wartość, która wskazuje stan operacji asynchronicznej.

## <a name="syntax"></a>Składnia

```cpp
STDMETHOD(
   get_Status
)(AsyncStatus *status) override;
```

### <a name="parameters"></a>Parametry

*status*<br/>
Lokalizacja, w których stan ma być przechowywany. Aby uzyskać więcej informacji, zobacz `Windows::Foundation::AsyncStatus` wyliczenia.

## <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie E_ILLEGAL_METHOD_CALL.

## <a name="remarks"></a>Uwagi

Ta metoda implementuje `IAsyncInfo::get_Status`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** async.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[AsyncBase, klasa](../windows/asyncbase-class.md)