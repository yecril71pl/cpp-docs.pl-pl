---
title: _com_error::GUID
ms.date: 11/04/2016
f1_keywords:
- _com_error::GUID
helpviewer_keywords:
- GUID method [C++]
ms.assetid: e84c2c23-d02e-48f8-b776-9bd6937296d2
ms.openlocfilehash: 905b67577a65b81be0b4d18c7513652dd8c5f055
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661633"
---
# <a name="comerrorguid"></a>_com_error::GUID

**Microsoft Specific**

Wywołania `IErrorInfo::GetGUID` funkcji.

## <a name="syntax"></a>Składnia

```
GUID GUID( ) const throw( );
```

## <a name="return-value"></a>Wartość zwracana

Zwraca wynik `IErrorInfo::GetGUID` dla `IErrorInfo` obiektu rejestrować się w ramach `_com_error` obiektu. Jeśli nie `IErrorInfo` obiektu jest rejestrowane, zwraca `GUID_NULL`.

## <a name="remarks"></a>Uwagi

Jakiekolwiek niepowodzenie podczas wywoływania `IErrorInfo::GetGUID` metody jest ignorowana.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[_com_error, klasa](../cpp/com-error-class.md)