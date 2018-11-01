---
title: _com_error::WCodeToHRESULT
ms.date: 11/04/2016
f1_keywords:
- _com_error::WCodeToHRESULT
helpviewer_keywords:
- WCodeToHRESULT method [C++]
ms.assetid: 0ec43a4b-ca91-42d5-b270-3fde9c8412ea
ms.openlocfilehash: f2fc84be53d95754d21c30eaea8dd981447453d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593071"
---
# <a name="comerrorwcodetohresult"></a>_com_error::WCodeToHRESULT

**Microsoft Specific**

Mapuje 16-bitowych *wcode —* HRESULT 32-bitowych.

## <a name="syntax"></a>Składnia

```
static HRESULT WCodeToHRESULT(
   WORD wCode
) throw( );
```

#### <a name="parameters"></a>Parametry

*Wcode —*<br/>
16-bitowych *wcode —* mają być mapowane na HRESULT 32-bitowych.

## <a name="return-value"></a>Wartość zwracana

32-bitowych HRESULT mapowane z 16-bitowych *wcode —*.

## <a name="remarks"></a>Uwagi

Zobacz [wcode —](../cpp/com-error-wcode.md) funkcja elementu członkowskiego.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[_com_error::WCode](../cpp/com-error-wcode.md)<br/>
[_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)<br/>
[_com_error, klasa](../cpp/com-error-class.md)