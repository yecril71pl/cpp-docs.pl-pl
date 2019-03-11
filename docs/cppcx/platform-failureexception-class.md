---
title: Platform::FailureException, klasa
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::FailureException::FailureException
- VCCORLIB/Platform::FailureException
helpviewer_keywords:
- Platform::FailureException
ms.assetid: 1729cd07-bfc2-448e-9db5-185d5cbf5b81
ms.openlocfilehash: f527271b50382a9aec1585e139a0083135315473
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750327"
---
# <a name="platformfailureexception-class"></a>Platform::FailureException, klasa

Element zgłaszany, gdy operacja nie powiodła się. Jest odpowiednikiem E_FAIL HRESULT.

## <a name="syntax"></a>Składnia

```cpp
public ref class FailureException : COMException,    IException,    IPrintable,    IEquatable
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [COMException](../cppcx/platform-comexception-class.md) klasy.

### <a name="requirements"></a>Wymagania

**Minimalna obsługiwana klienta:** Windows 8

**Minimalna obsługiwana serwera:** Windows Server 2012

**Namespace:** Platforma

**Metadane:** platform.winmd

## <a name="see-also"></a>Zobacz także

[Platform::COMException, klasa](../cppcx/platform-comexception-class.md)
