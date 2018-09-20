---
title: AsyncBase::GetOnComplete, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::GetOnComplete
dev_langs:
- C++
helpviewer_keywords:
- GetOnComplete method
ms.assetid: f06ae02d-9a88-41d2-b749-bdc1a7ff8748
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f9e6ee8da9c30ca3d5da9f772e46beca76f424be
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46398446"
---
# <a name="asyncbasegetoncomplete-method"></a>AsyncBase::GetOnComplete — Metoda

Kopiuje adres bieżącej obsługi zdarzeń zakończenia do określonej zmiennej.

## <a name="syntax"></a>Składnia

```cpp
STDMETHOD(
   GetOnComplete
)(TComplete** completeHandler);
```

### <a name="parameters"></a>Parametry

*completeHandler*<br/>
Lokalizacja przechowywania adres bieżącej obsługi zdarzeń zakończenia.

## <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie E_ILLEGAL_METHOD_CALL.

## <a name="requirements"></a>Wymagania

**Nagłówek:** async.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[AsyncBase, klasa](../windows/asyncbase-class.md)