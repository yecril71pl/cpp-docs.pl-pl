---
title: Struktura WINDOWPLACEMENT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- WINDOWPLACEMENT
dev_langs:
- C++
helpviewer_keywords:
- WINDOWPLACEMENT structure [MFC]
ms.assetid: ea7d61f6-eb57-478e-9b08-7c1d07091aa8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b163d93de22d313d72ca5dbfd384788077ae1b01
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46447280"
---
# <a name="windowplacement-structure"></a>Struktura WINDOWPLACEMENT

`WINDOWPLACEMENT` Struktura zawiera informacje dotyczące położenia okna na ekranie.

## <a name="syntax"></a>Składnia

```
typedef struct tagWINDOWPLACEMENT {     /* wndpl */
    UINT length;
    UINT flags;
    UINT showCmd;
    POINT ptMinPosition;
    POINT ptMaxPosition;
    RECT rcNormalPosition;
} WINDOWPLACEMENT;
```

#### <a name="parameters"></a>Parametry

*Długość*<br/>
Określa długość w bajtach, struktury.

*flagi*<br/>
Określa flagi, które sterują położeniem zminimalizowanego okna, a także metoda, za pomocą którego jest przywracany okna. Ten element członkowski może być jeden lub oba z następujących flag:

- WPF_SETMINPOSITION Określa, że można określić pozycji x i y zminimalizowane okno. Ta flaga musi być określona, jeśli współrzędne są ustawiane w `ptMinPosition` elementu członkowskiego.

- WPF_RESTORETOMAXIMIZED Określa, że przywróconych okno będzie zmaksymalizowane, niezależnie od tego, czy został zmaksymalizowane, zanim został on zminimalizowany. To ustawienie jest prawidłowy tylko podczas następnego okna jest przywracany. Nie zmienia domyślne zachowanie przywracania. Ta flaga jest prawidłowy tylko wtedy, gdy określona jest wartość SW_SHOWMINIMIZED dla `showCmd` elementu członkowskiego.

*showCmd*<br/>
Określa bieżący stan Pokaż okna. Ten element członkowski może być jednym z następujących wartości:

- SW_HIDE ukrywa okno i przekazuje aktywacji do innego okna.

- SW_MINIMIZE minimalizuje określone okno i aktywuje okno najwyższego poziomu, na liście systemu.

- Aktywuje SW_RESTORE i wyświetla okno. Jeśli okno jest zminimalizowane lub zmaksymalizowane, Windows przywraca oryginalny rozmiar i położenie (tak jak SW_SHOWNORMAL).

- SW_SHOW aktywuje okno i wyświetla go w jego bieżący rozmiar i położenie.

- SW_SHOWMAXIMIZED aktywuje okno i wyświetla je jako zmaksymalizowane okno.

- SW_SHOWMINIMIZED aktywuje okno i wyświetla je jako ikona.

- SW_SHOWMINNOACTIVE wyświetli okno jako ikona. Okno, które jest obecnie aktywny pozostaje aktywna.

- SW_SHOWNA wyświetli okno w jego bieżącym stanie. Okno, które jest obecnie aktywny pozostaje aktywna.

- SW_SHOWNOACTIVATE wyświetli okno w najnowszych rozmiar i położenie. Okno, które jest obecnie aktywny pozostaje aktywna.

- Aktywuje SW_SHOWNORMAL i wyświetla okno. Jeśli okno jest zminimalizowane lub zmaksymalizowane, Windows przywraca oryginalny rozmiar i położenie (tak jak SW_RESTORE).

*ptMinPosition*<br/>
Określa położenie w lewym górnym rogu okna, gdy okno jest zminimalizowana.

*ptMaxPosition*<br/>
Określa położenie w lewym górnym rogu okna, gdy okno jest zmaksymalizowane.

*rcNormalPosition*<br/>
Określa współrzędne okna, gdy okno jest w normalnych pozycji (przywróconej).

## <a name="requirements"></a>Wymagania

**Nagłówek:** winuser.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::SetWindowPlacement](../../mfc/reference/cwnd-class.md#setwindowplacement)

