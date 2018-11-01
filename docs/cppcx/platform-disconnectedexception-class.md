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
ms.openlocfilehash: 2d4f8f4cb52fdb7e50c36eb3f0255bd85c15dbb1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477145"
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