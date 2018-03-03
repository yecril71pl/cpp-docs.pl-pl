---
title: Struktura SOCKADDR | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SOCKADDR
dev_langs:
- C++
helpviewer_keywords:
- SOCKADDR structure [MFC]
ms.assetid: df1ed66a-f4b8-43f8-8db8-8c2533d25f68
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 55b310ec83aae35c7386d61849663752811651d4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="sockaddr-structure"></a>Struktura SOCKADDR
`SOCKADDR` Struktury jest używany do przechowywania adres protokołu internetowego (IP) dla komputera, należący do komunikacji usługi Windows Sockets.  
  
## <a name="syntax"></a>Składnia  
  
```  
struct sockaddr {  
    unsigned short sa_family;  
    char sa_data[14];  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 *sa_family*  
 Rodziną adresów gniazd.  
  
 *sa_data*  
 Maksymalny rozmiar wszystkich elementów adresu innego gniazda.  
  
## <a name="remarks"></a>Uwagi  
 Zestaw dewelopera Microsoft TCP/IP Sockets obsługuje tylko domen adresów internetowych. Aby wypełnić faktycznie wartości dla każdej części adresu, należy użyć `SOCKADDR_IN` struktury danych, która jest specjalnie dla następującego formatu adresu. `SOCKADDR` i `SOCKADDR_IN` struktury danych mają taki sam rozmiar. Po prostu rzutować przełączać się między typami dwie struktury.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** winsock2.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [Sockaddr_in — struktura](../../mfc/reference/sockaddr-in-structure.md)   
 [CAsyncSocket::Create](../../mfc/reference/casyncsocket-class.md#create)   
 [CSocket::Create](../../mfc/reference/csocket-class.md#create)

