---
title: Struktura MSG
ms.date: 11/04/2016
f1_keywords:
- MSG
helpviewer_keywords:
- MSG structure [MFC]
ms.assetid: dc166d27-9423-41f1-9599-5ba76d2f0138
ms.openlocfilehash: 1a953f8d0d685e25beedd2d401e227c934414208
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499818"
---
# <a name="msg-structure"></a>Struktura MSG

`MSG` Struktura zawiera informacje o wiadomości z kolejki komunikatów dla wątku.

## <a name="syntax"></a>Składnia

```
typedef struct tagMSG {     // msg
    HWND hwnd;
    UINT message;
    WPARAM wParam;
    LPARAM lParam;
    DWORD time;
    POINT pt;
} MSG;
```

#### <a name="parameters"></a>Parametry

*hwnd*<br/>
Identyfikuje okna, w których procedurę okna odbiera komunikat.

*komunikat*<br/>
Określa numer komunikatu.

*wParam*<br/>
Określa dodatkowe informacje na temat wiadomości. Dokładne znaczenie zależy od wartości `message` elementu członkowskiego.

*lParam*<br/>
Określa dodatkowe informacje na temat wiadomości. Dokładne znaczenie zależy od wartości `message` elementu członkowskiego.

*czas*<br/>
Określa czas, w którym opublikowano wiadomość.

*(czas pacyficzny)*<br/>
Określa położenie kursora, we współrzędnych ekranu, gdy opublikowano wiadomość.

## <a name="requirements"></a>Wymagania

**Nagłówek:** winuser.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

