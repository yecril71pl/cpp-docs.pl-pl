---
title: _com_error::HRESULTToWCode
ms.date: 11/04/2016
f1_keywords:
- _com_error::HRESULTToWCode
helpviewer_keywords:
- HRESULTToWCode method [C++]
ms.assetid: ff3789f5-1047-41a0-b7e3-86dd8f638dba
ms.openlocfilehash: 35a497c273f15c9755d3607e7907a3a48dad8dc8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180566"
---
# <a name="_com_errorhresulttowcode"></a>_com_error::HRESULTToWCode

**Specyficzne dla firmy Microsoft**

Odwzorowuje 32-bitowy wynik HRESULT na 16-bitowy `wCode`.

## <a name="syntax"></a>Składnia

```
static WORD HRESULTToWCode(
   HRESULT hr
) throw( );
```

#### <a name="parameters"></a>Parametry

*wysoki*<br/>
32-bitowy wynik HRESULT ma zostać zmapowany na 16-bitowy `wCode`.

## <a name="return-value"></a>Wartość zwracana

16-bitowe `wCode` mapowane z 32-bitowej HRESULT.

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [_com_error:: kodostrzeżenia](../cpp/com-error-wcode.md) .

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[_com_error::WCode](../cpp/com-error-wcode.md)<br/>
[_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)<br/>
[_com_error, klasa](../cpp/com-error-class.md)
