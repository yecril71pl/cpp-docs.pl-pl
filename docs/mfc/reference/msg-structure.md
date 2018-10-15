---
title: Struktura MSG | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- MSG
dev_langs:
- C++
helpviewer_keywords:
- MSG structure [MFC]
ms.assetid: dc166d27-9423-41f1-9599-5ba76d2f0138
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2b2f58af3bcf3eef524b95d25579e5bc233f9108
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2018
ms.locfileid: "49334448"
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

