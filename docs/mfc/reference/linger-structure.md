---
title: Struktura LINGER
ms.date: 11/04/2016
f1_keywords:
- LINGER
helpviewer_keywords:
- LINGER structure [MFC]
ms.assetid: 1fb1c5bf-a64e-4a6c-89d6-1734e4fdbb1b
ms.openlocfilehash: 78f1a5ce993373ea9e477262f0779515c52dbd8c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50495321"
---
# <a name="linger-structure"></a>Struktura LINGER

`LINGER` Struktura jest używana do manipulowania opcje SO_LINGER i SO_DONTLINGER `CAsyncSocket::GetSockOpt`.

## <a name="syntax"></a>Składnia

```
struct linger {
    u_short l_onoff;            // option on/off
    u_short l_linger;           // linger time
};
```

## <a name="remarks"></a>Uwagi

Ustawianie opcji SO_DONTLINGER zapobiega blokowania na funkcję członkowską `Close` podczas oczekiwania na niewysłanych danych do wysłania. Ustawienie tej opcji jest równoznaczne z ustawieniem SO_LINGER z `l_onoff` ustawione na 0.

## <a name="requirements"></a>Wymagania

**Nagłówek:** winsock2.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CAsyncSocket::GetSockOpt](../../mfc/reference/casyncsocket-class.md#getsockopt)<br/>
[CAsyncSocket::SetSockOpt](../../mfc/reference/casyncsocket-class.md#setsockopt)

