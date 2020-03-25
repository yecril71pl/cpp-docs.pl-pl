---
title: _com_error::WCodeToHRESULT
ms.date: 11/04/2016
f1_keywords:
- _com_error::WCodeToHRESULT
helpviewer_keywords:
- WCodeToHRESULT method [C++]
ms.assetid: 0ec43a4b-ca91-42d5-b270-3fde9c8412ea
ms.openlocfilehash: f2194e0e54a93d3227b84d893f9d3f208d972d09
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180514"
---
# <a name="_com_errorwcodetohresult"></a>_com_error::WCodeToHRESULT

**Specyficzne dla firmy Microsoft**

Maps 16-bitowy *kodostrzeżenia* do 32-bitowy wynik HRESULT.

## <a name="syntax"></a>Składnia

```
static HRESULT WCodeToHRESULT(
   WORD wCode
) throw( );
```

#### <a name="parameters"></a>Parametry

*Kodostrzeżenia*<br/>
16-bitowa *kodostrzeżenia* do zmapowania na 32-bitowy wynik HRESULT.

## <a name="return-value"></a>Wartość zwracana

32-bitowe HRESULT zamapowane z 16-bitowej *kodostrzeżenia*.

## <a name="remarks"></a>Uwagi

Zobacz funkcję członkowską [kodostrzeżenia](../cpp/com-error-wcode.md) .

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[_com_error::WCode](../cpp/com-error-wcode.md)<br/>
[_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)<br/>
[_com_error, klasa](../cpp/com-error-class.md)
