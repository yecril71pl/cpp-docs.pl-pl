---
title: Platform::DisconnectedException, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::DisconnectedException
- VCCORLIB/Platform::DisconnectedException::DisconnectedException
dev_langs:
- C++
helpviewer_keywords:
- Platform::DisconnectedException
ms.assetid: c25e0d64-5bff-4c21-88e5-c4ec2776fa7f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a84d07db2e3fe48d981641d2803352d90268d93a
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43754068"
---
# <a name="platformdisconnectedexception-class"></a>Platform::DisconnectedException, klasa
Zgłaszany, gdy próbuje odwoływać się do serwera COM, który nie istnieje już obiekt serwera proxy modelu COM  
  
## <a name="syntax"></a>Składnia  
  
```  
public ref class DisconnectedException : COMException,    IException,    IPrintable,    IEquatable  
```  
  
### <a name="remarks"></a>Uwagi  
 Gdy innej klasy (klasy B), który znajduje się w oddzielnym procesie klasy A wymaga obiektu serwera proxy do komunikacji z serwerem modelu COM spoza procesu A odwołań do klas zawierający klasy B. Czasami serwera wykroczyć poza pamięci bez klasy jego wiedzy. W takim przypadku jest zgłaszany wyjątek RPC_E_DISCONNECTED i pobiera tłumaczone Platform::DisconnectedException. Jeden scenariusz, w którym jest występuje sytuacja, źródła zdarzeń wywołuje delegata, który został przekazany do niego, ale delegata został zniszczony w pewnym momencie po subskrypcję zdarzenia. W takim przypadku źródło zdarzenia usuwa delegata z listy jej wywołania.  
  
 Aby uzyskać więcej informacji, zobacz [COMException](../cppcx/platform-comexception-class.md) klasy.  
  
### <a name="requirements"></a>Wymagania  
 **Minimalna obsługiwana klienta:** systemu Windows 8  
  
 **Minimalna obsługiwana serwera:** systemu Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Metadane:** platform.winmd  
  
## <a name="see-also"></a>Zobacz też  
 [Platform::COMException, klasa](../cppcx/platform-comexception-class.md)