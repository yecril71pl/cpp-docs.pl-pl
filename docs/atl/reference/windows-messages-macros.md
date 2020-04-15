---
title: Makra wiadomości systemu Windows
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::WM_FORWARDMSG
ms.assetid: 63abd22c-372d-4148-bb04-c605950ae64f
ms.openlocfilehash: a5a6d45c64d6123128ae362c1ef5643392439f41
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329408"
---
# <a name="windows-messages-macros"></a>Makra wiadomości systemu Windows

To makro przekazuje wiadomości okienne.

|||
|-|-|
|[WM_FORWARDMSG](#wm_forwardmsg)|Służy do przesyłania dalej wiadomości odebranej przez okno do innego okna do przetwarzania.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="wm_forwardmsg"></a><a name="wm_forwardmsg"></a>WM_FORWARDMSG

To makro przekazuje wiadomość odebraną przez okno do innego okna w celu przetworzenia.

```
WM_FORWARDMSG
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wiadomość została przetworzona, zero, jeśli nie.

### <a name="remarks"></a>Uwagi

Użyj WM_FORWARDMSG, aby przesłać dalej wiadomość odebraną przez okno do innego okna do przetworzenia. Parametry LPARAM i WPARAM są używane w następujący sposób:

|Parametr|Sposób użycia|
|---------------|-----------|
|Wparam|Dane zdefiniowane przez użytkownika|
|Lparam|Wskaźnik do `MSG` struktury zawierającej informacje o wiadomości|

### <a name="example"></a>Przykład

W poniższym `m_hWndOther` przykładzie reprezentuje inne okno, które odbiera ten komunikat.

[!code-cpp[NVC_ATL_Windowing#137](../../atl/codesnippet/cpp/windows-messages-macros_1.cpp)]

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)
