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
ms.openlocfilehash: f468a0a68dcfedab3b92deea492b48f7876c1610
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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

