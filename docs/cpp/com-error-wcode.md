---
title: _com_error::WCode
ms.date: 11/04/2016
f1_keywords:
- _com_error::WCode
helpviewer_keywords:
- WCode method [C++]
ms.assetid: f3b21852-f8ea-4e43-bff1-11c2d35454c4
ms.openlocfilehash: 92dffbdbe034ef55be04c1b7d204be6880d8d4b2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190199"
---
# <a name="_com_errorwcode"></a>_com_error::WCode

**Specyficzne dla firmy Microsoft**

Pobiera 16-bitowy kod błędu mapowany na hermetyzowaną wartość HRESULT.

## <a name="syntax"></a>Składnia

```
WORD WCode ( ) const throw( );
```

## <a name="return-value"></a>Wartość zwracana

Jeśli wynik HRESULT znajduje się w zakresie od 0x80040200 do 0x8004FFFF, Metoda `WCode` zwraca wynik HRESULT minus 0x80040200; w przeciwnym razie zwraca wartość zero.

## <a name="remarks"></a>Uwagi

Metoda `WCode` służy do cofania mapowania, które odbywa się w kodzie obsługi COM. Otoka dla właściwości `dispinterface` lub metody wywołuje procedurę obsługi, która pakuje argumenty i wywołania `IDispatch::Invoke`. Po powrocie, jeśli zostanie zwrócona wartość HRESULT dla `DISP_E_EXCEPTION`, zostaną pobrane informacje o błędzie ze struktury `EXCEPINFO` przekazana do `IDispatch::Invoke`. Kod błędu może być 16-bitową wartością przechowywaną w `wCode` składowej struktury `EXCEPINFO` lub pełną 32-bitową wartość w `scode` elemencie członkowskim struktury `EXCEPINFO`. Jeśli zostanie zwrócona `wCode` 16-bitowa, musi ona zostać najpierw zmapowana na 32-bitową awarię HRESULT.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)<br/>
[_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)<br/>
[_com_error, klasa](../cpp/com-error-class.md)
