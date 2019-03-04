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
ms.openlocfilehash: d6e3168b5c86de5bce3c3b9d3b0fbdea28ae604f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57286931"
---
# <a name="atlcreatewnddata-structure"></a>Struktura _AtlCreateWndData

Ta struktura zawiera dane wystąpienia klasy w kodzie obsługi okien w ATL.

## <a name="syntax"></a>Składnia

```
    struct _AtlCreateWndData{
    void* m_pThis;
    DWORD m_dwThreadID;
    _AtlCreateWndData* m_pNext;
};
```

## <a name="members"></a>Elementy członkowskie

`m_pThis`<br/>
**To** wskaźnik używany do uzyskiwania dostępu do wystąpienia klasy w procedury okna.

`m_dwThreadID`<br/>
Identyfikator wątku bieżącego wystąpienia klasy.

`m_pNext`<br/>
Wskaźnik do następnego `_AtlCreateWndData` obiektu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="see-also"></a>Zobacz także

[Klasy i struktury](../../atl/reference/atl-classes.md)
