---
title: Struktura SOCKADDR
ms.date: 11/04/2016
f1_keywords:
- SOCKADDR
helpviewer_keywords:
- SOCKADDR structure [MFC]
ms.assetid: df1ed66a-f4b8-43f8-8db8-8c2533d25f68
ms.openlocfilehash: 68d5261c6520b5baee8495b72a0b9d234a35a185
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543848"
---
# <a name="sockaddr-structure"></a>Struktura SOCKADDR

`SOCKADDR` Struktury jest używany do przechowywania adres protokołu internetowego (IP) dla maszyny z uczestnictwa w komunikacie Windows Sockets.

## <a name="syntax"></a>Składnia

```
struct sockaddr {
    unsigned short sa_family;
    char sa_data[14];
};
```

#### <a name="parameters"></a>Parametry

*sa_family*<br/>
Rodzina adresów gniazda.

*sa_data*<br/>
Maksymalny rozmiar wszystkich elementów adresu innego gniazda.

## <a name="remarks"></a>Uwagi

Zestaw dewelopera gniazda TCP/IP firmy Microsoft obsługuje tylko domeny adresów internetowych. Aby rzeczywiście Podaj wartości dla każdej części adresu, należy użyć `SOCKADDR_IN` struktury danych, który jest specjalnie dla następującego formatu adresu. `SOCKADDR` i `SOCKADDR_IN` struktur danych mają taki sam rozmiar. Rzutowanie jest po prostu przełączać się między typami dwie struktury.

## <a name="requirements"></a>Wymagania

**Nagłówek:** winsock2.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[Struktura SOCKADDR_IN](../../mfc/reference/sockaddr-in-structure.md)<br/>
[CAsyncSocket::Create](../../mfc/reference/casyncsocket-class.md#create)<br/>
[CSocket::Create](../../mfc/reference/csocket-class.md#create)

