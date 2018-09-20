---
title: Struktura SOCKADDR | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- SOCKADDR
dev_langs:
- C++
helpviewer_keywords:
- SOCKADDR structure [MFC]
ms.assetid: df1ed66a-f4b8-43f8-8db8-8c2533d25f68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac6e433c0bbc70e6e1caa79599d5388aef49b4c5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435288"
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

