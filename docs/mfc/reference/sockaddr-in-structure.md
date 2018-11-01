---
title: SOCKADDR_IN — Struktura
ms.date: 11/04/2016
f1_keywords:
- SOCKADDR_IN
helpviewer_keywords:
- SOCKADDR_IN structure [MFC]
ms.assetid: e8cd7c34-78bd-4e28-a990-eb3ca070b7a6
ms.openlocfilehash: 22d02b2e3c6fd7151e59cad0f3233539c04a16e0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431229"
---
# <a name="sockaddrin-structure"></a>SOCKADDR_IN — Struktura

W rodzinie adresów internetowych `SOCKADDR_IN` struktury jest używany przez Windows Sockets do określenia adresu lokalnego lub zdalnego punktu końcowego, do którego ma zostać połączenia gniazda.

## <a name="syntax"></a>Składnia

```
struct sockaddr_in{
    short sin_family;
    unsigned short sin_port;
struct in_addr sin_addr;
    char sin_zero[8];
};
```

#### <a name="parameters"></a>Parametry

*sin_family*<br/>
Rodzina adresów (musi być AF_INET).

*sin_port*<br/>
Port adresu IP.

*sin_addr*<br/>
Adres IP.

*sin_zero*<br/>
Wypełnienie w celu uzyskania struktury taki sam rozmiar jak `SOCKADDR`.

## <a name="remarks"></a>Uwagi

To jest to forma `SOCKADDR` struktury specyficzne dla internetowej rodziny adresowej i może być rzutowany `SOCKADDR`.

Składnik adresu IP tej struktury jest typu `IN_ADDR`. `IN_ADDR` Struktura jest zdefiniowana w pliku nagłówkowym Windows Sockets WINSOCK. H w następujący sposób:

```
struct in_addr {
    union {
        struct {
            unsigned char s_b1, s_b2, s_b3, s_b4;
        } S_un_b;
        struct {
            unsigned short s_w1, s_w2;
        } S_un_w;
        unsigned long S_addr;
    } S_un;
};
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** winsock2.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[Struktura SOCKADDR](../../mfc/reference/sockaddr-structure.md)
