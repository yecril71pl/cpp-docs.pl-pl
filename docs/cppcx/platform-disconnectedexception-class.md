---
title: Platform::DisconnectedException, klasa
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::DisconnectedException
- VCCORLIB/Platform::DisconnectedException::DisconnectedException
helpviewer_keywords:
- Platform::DisconnectedException
ms.assetid: c25e0d64-5bff-4c21-88e5-c4ec2776fa7f
ms.openlocfilehash: 56276a7d09cc82e05886c2c67a4784993083adb5
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57752015"
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

**Minimalna obsługiwana klienta:** Windows 8

**Minimalna obsługiwana serwera:** Windows Server 2012

**Namespace:** Platforma

**Metadane:** platform.winmd

## <a name="see-also"></a>Zobacz także

[Platform::COMException, klasa](../cppcx/platform-comexception-class.md)
