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
ms.openlocfilehash: aeb9e61f94ddd5f41ff3de26728c1fbe155f809d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33373641"
---
# <a name="sockaddrin-structure"></a>SOCKADDR_IN — Struktura
W rodzinie adresu internetowego `SOCKADDR_IN` struktury jest używany przez usługi Windows Sockets, aby określić adres lokalny lub zdalny punkt końcowy do połączenia gniazda.  
  
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
 Rodzina adresów (musi być **AF_INET**).  
  
 *sin_port*  
 IP port.  
  
 *sin_addr*  
 Adres IP.  
  
 *sin_zero*  
 Dopełnienie dokonanie struktury taki sam rozmiar jak `SOCKADDR`.  
  
## <a name="remarks"></a>Uwagi  
 Jest to formę `SOCKADDR` struktury specyficzne dla rodziny adresów internetowych i mogą być rzutowane na `SOCKADDR`.  
  
 Ta struktura składnika adres IP jest typu **IN_ADDR**. **IN_ADDR** struktury jest zdefiniowana w pliku nagłówka Windows Sockets WINSOCK. H w następujący sposób:  
  
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
