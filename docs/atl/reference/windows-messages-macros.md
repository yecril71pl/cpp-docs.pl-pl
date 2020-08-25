---
title: Makra komunikatów systemu Windows
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::WM_FORWARDMSG
ms.assetid: 63abd22c-372d-4148-bb04-c605950ae64f
ms.openlocfilehash: b4cd3c2eea24449eb17050b147d9c59560d8358f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834443"
---
# <a name="windows-messages-macros"></a>Makra komunikatów systemu Windows

To makro przesyła dalej komunikaty systemu Windows.

|Nazwa|Opis|
|-|-|
|[WM_FORWARDMSG](#wm_forwardmsg)|Służy do przesyłania dalej wiadomości odebranej przez okno do innego okna do przetworzenia.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

## <a name="wm_forwardmsg"></a><a name="wm_forwardmsg"></a> WM_FORWARDMSG

To makro przekazuje komunikat otrzymany przez okno do innego okna do przetworzenia.

```
WM_FORWARDMSG
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli wiadomość została przetworzona, zero, jeśli nie.

### <a name="remarks"></a>Uwagi

Użyj WM_FORWARDMSG, aby przesłać wiadomość odebraną przez okno do innego okna do przetworzenia. Parametry LPARAM i WPARAM są używane w następujący sposób:

|Parametr|Użycie|
|---------------|-----------|
|WPARAM|Dane zdefiniowane przez użytkownika|
|LPARAM|Wskaźnik do struktury zawierającej `MSG` Informacje o wiadomości|

### <a name="example"></a>Przykład

W poniższym przykładzie `m_hWndOther` reprezentuje inne okno, które odbiera ten komunikat.

[!code-cpp[NVC_ATL_Windowing#137](../../atl/codesnippet/cpp/windows-messages-macros_1.cpp)]

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)
