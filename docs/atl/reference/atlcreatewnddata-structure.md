---
title: Struktura _AtlCreateWndData
ms.date: 11/04/2016
f1_keywords:
- ATL::_AtlCreateWndData
- ATL._AtlCreateWndData
- _AtlCreateWndData
helpviewer_keywords:
- _AtlCreateWndData structure
- AtlCreateWndData structure
ms.assetid: 76ed5382-bfbf-4b8b-8a29-912688dfd2ae
ms.openlocfilehash: 6453156a59b73bcb06c7c86920e1dc524874cef8
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168543"
---
# <a name="_atlcreatewnddata-structure"></a>Struktura _AtlCreateWndData

Ta struktura zawiera dane wystąpienia klasy w kodzie systemu Windows w ATL.

## <a name="syntax"></a>Składnia

```cpp
    struct _AtlCreateWndData{
    void* m_pThis;
    DWORD m_dwThreadID;
    _AtlCreateWndData* m_pNext;
};
```

## <a name="members"></a>Elementy członkowskie

`m_pThis`<br/>
Wskaźnik **używany** do uzyskania dostępu do wystąpienia klasy w procedurach okna.

`m_dwThreadID`<br/>
Identyfikator wątku bieżącego wystąpienia klasy.

`m_pNext`<br/>
Wskaźnik do następnego `_AtlCreateWndData` obiektu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

## <a name="see-also"></a>Zobacz także

[Klasy i struktury](../../atl/reference/atl-classes.md)
