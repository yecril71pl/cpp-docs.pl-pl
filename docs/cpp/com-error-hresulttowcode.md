---
title: _com_error::HRESULTToWCode | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::HRESULTToWCode
dev_langs:
- C++
helpviewer_keywords:
- HRESULTToWCode method [C++]
ms.assetid: ff3789f5-1047-41a0-b7e3-86dd8f638dba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c39b638451aa8ea89191e323eae5f2c140563990
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082069"
---
# <a name="comerrorhresulttowcode"></a>_com_error::HRESULTToWCode

**Microsoft Specific**

Mapuje HRESULT 32-bitowego do 16-bitowych `wCode`.

## <a name="syntax"></a>Składnia

```
static WORD HRESULTToWCode(
   HRESULT hr
) throw( );
```

#### <a name="parameters"></a>Parametry

*godz.*<br/>
HRESULT 32-bitowe mają być mapowane do 16-bitowych `wCode`.

## <a name="return-value"></a>Wartość zwracana

16-bitowych `wCode` mapowane z HRESULT 32-bitowych.

## <a name="remarks"></a>Uwagi

Zobacz [_com_error::WCode](../cpp/com-error-wcode.md) Aby uzyskać więcej informacji.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[_com_error::WCode](../cpp/com-error-wcode.md)<br/>
[_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)<br/>
[_com_error, klasa](../cpp/com-error-class.md)