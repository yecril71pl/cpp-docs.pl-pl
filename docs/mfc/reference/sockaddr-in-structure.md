---
title: Sockaddr_in — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- SOCKADDR_IN
dev_langs:
- C++
helpviewer_keywords:
- SOCKADDR_IN structure [MFC]
ms.assetid: e8cd7c34-78bd-4e28-a990-eb3ca070b7a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5e5ec6ebf4329ff03c75240dc7cec93e9ba46331
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37885741"
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
 *sin_family*  
 Rodzina adresów (musi być AF_INET).  
  
 *sin_port*  
 Port adresu IP.  
  
 *sin_addr*  
 Adres IP.  
  
 *sin_zero*  
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
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [Struktura SOCKADDR](../../mfc/reference/sockaddr-structure.md)
