---
title: Makra komunikatów Windows
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::WM_FORWARDMSG
ms.assetid: 63abd22c-372d-4148-bb04-c605950ae64f
ms.openlocfilehash: 7bb5e2fa265c3a5dcabcc16d8343d5b86a4aaf42
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273927"
---
# <a name="windows-messages-macros"></a>Makra komunikatów Windows

To makro przekazuje komunikaty okna.

|||
|-|-|
|[WM_FORWARDMSG](#wm_forwardmsg)|Użyj, aby przesłać dalej wiadomość zostaje odebrana przez okno do innego okna do przetworzenia.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

##  <a name="wm_forwardmsg"></a>  WM_FORWARDMSG

To makro przesyła wiadomość zostaje odebrana przez okno do innego okna do przetworzenia.

```
WM_FORWARDMSG
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera jeśli komunikat został przetworzony, zero, jeśli nie.

### <a name="remarks"></a>Uwagi

Użyj WM_FORWARDMSG, aby przesłać dalej wiadomość zostaje odebrana przez okno do innego okna do przetworzenia. Parametry LPARAM i WPARAM są używane w następujący sposób:

|Parametr|Użycie|
|---------------|-----------|
|WPARAM|Dane zdefiniowane przez użytkownika|
|LPARAM|Wskaźnik do `MSG` strukturę, która zawiera informacje o wiadomości|

### <a name="example"></a>Przykład

W poniższym przykładzie `m_hWndOther` reprezentuje okna, który odbiera ten komunikat.

[!code-cpp[NVC_ATL_Windowing#137](../../atl/codesnippet/cpp/windows-messages-macros_1.cpp)]

## <a name="see-also"></a>Zobacz także

[Makra](../../atl/reference/atl-macros.md)
