---
title: Klasa platform::DisconnectedException | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- VCCORLIB/Platform::DisconnectedException
- VCCORLIB/Platform::DisconnectedException::DisconnectedException
dev_langs: C++
helpviewer_keywords: Platform::DisconnectedException
ms.assetid: c25e0d64-5bff-4c21-88e5-c4ec2776fa7f
caps.latest.revision: "4"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e9ce20c019c022ed62c2be888617b387315731b8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="platformdisconnectedexception-class"></a>Klasa platform::DisconnectedException
Element zgłaszany, gdy obiekt serwera proxy modelu COM próbuje odwołać serwer COM, który już nie istnieje  
  
## <a name="syntax"></a>Składnia  
  
```  
public ref class DisconnectedException : COMException,    IException,    IPrintable,    IEquatable  
```  
  
### <a name="remarks"></a>Uwagi  
 Gdy obiekt serwera proxy do komunikacji z serwerem COM poza procesem wymaga innej klasy (klasa B), który znajduje się w osobnych procesach klasy A odwołuje się do klasy A przechowuje klasy B. Czasami serwera można przejść za mało pamięci bez klasy wiedzy. W takim przypadku jest zwracany wyjątek RPC_E_DISCONNECTED i pobiera translacji Platform::DisconnectedException. Jest jeden scenariusz, w którym występuje jest źródłem zdarzeń wywołuje delegata, który został przekazany do niego, ale delegat został zlikwidowany w pewnym momencie po jej subskrybuje zdarzenia. W takim przypadku źródło zdarzenia usuwa tego delegata z listy jej wywołania.  
  
 Aby uzyskać więcej informacji, zobacz [COMException](../cppcx/platform-comexception-class.md) klasy.  
  
### <a name="requirements"></a>Wymagania  
 **Minimalna obsługiwana klienta:** systemu Windows 8  
  
 **Minimalna obsługiwana serwera:** systemu Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Metadane:** platform.winmd  
  
## <a name="see-also"></a>Zobacz też  
 [Platform::COMException, klasa](../cppcx/platform-comexception-class.md)