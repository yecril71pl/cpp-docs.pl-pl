---
title: FtmBase::DisconnectObject, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::DisconnectObject
dev_langs:
- C++
helpviewer_keywords:
- DisconnectObject method
ms.assetid: 33253eec-3a65-4e72-8525-0249245a4790
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b467162d2f5cc5b04bc43a6d31019eb08e17e750
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595409"
---
# <a name="ftmbasedisconnectobject-method"></a>FtmBase::DisconnectObject — Metoda

Wymuś zwalnia wszystkie połączenia zewnętrzne do obiektu. Serwer obiektu wywołuje obiekt implementacja tej metody przed zamykanie.

## <a name="syntax"></a>Składnia

```cpp
STDMETHODIMP DisconnectObject(
   __in DWORD dwReserved
) override;
```

### <a name="parameters"></a>Parametry

*dwReserved*  
Zarezerwowane dla przyszłego użytku; musi mieć wartość zero.

## <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.

## <a name="requirements"></a>Wymagania

**Nagłówek:** ftm.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[FtmBase, klasa](../windows/ftmbase-class.md)