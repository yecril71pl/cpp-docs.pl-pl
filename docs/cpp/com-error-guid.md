---
title: _com_error::GUID
ms.date: 11/04/2016
f1_keywords:
- _com_error::GUID
helpviewer_keywords:
- GUID method [C++]
ms.assetid: e84c2c23-d02e-48f8-b776-9bd6937296d2
ms.openlocfilehash: d5b05cd4e26f89d42ea23b605f5e6560795a0cfa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180644"
---
# <a name="_com_errorguid"></a>_com_error::GUID

**Specyficzne dla firmy Microsoft**

Wywołuje funkcję `IErrorInfo::GetGUID`.

## <a name="syntax"></a>Składnia

```
GUID GUID( ) const throw( );
```

## <a name="return-value"></a>Wartość zwracana

Zwraca wynik `IErrorInfo::GetGUID` dla obiektu `IErrorInfo` zarejestrowanego w obiekcie `_com_error`. Jeśli żaden obiekt `IErrorInfo` nie jest zarejestrowany, zwraca `GUID_NULL`.

## <a name="remarks"></a>Uwagi

Wystąpił błąd podczas wywoływania metody `IErrorInfo::GetGUID`.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[_com_error, klasa](../cpp/com-error-class.md)
