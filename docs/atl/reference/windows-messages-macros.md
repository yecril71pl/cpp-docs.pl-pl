---
title: Makra komunikatów Windows | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::WM_FORWARDMSG
dev_langs:
- C++
ms.assetid: 63abd22c-372d-4148-bb04-c605950ae64f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3f9d312104254323e98f6b2fd031adf1064ecfac
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078222"
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

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)
