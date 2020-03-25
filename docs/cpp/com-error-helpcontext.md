---
title: _com_error::HelpContext
ms.date: 11/04/2016
f1_keywords:
- _com_error::HelpContext
helpviewer_keywords:
- HelpContext method [C++]
ms.assetid: 160d6443-9b68-4cf5-a540-50da951a5b2b
ms.openlocfilehash: b3c79bb069ef504680e83359d6ec90c803f16d9d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180592"
---
# <a name="_com_errorhelpcontext"></a>_com_error::HelpContext

**Specyficzne dla firmy Microsoft**

Wywołuje funkcję `IErrorInfo::GetHelpContext`.

## <a name="syntax"></a>Składnia

```
DWORD HelpContext( ) const throw( );
```

## <a name="return-value"></a>Wartość zwracana

Zwraca wynik `IErrorInfo::GetHelpContext` dla obiektu `IErrorInfo` zarejestrowanego w obiekcie `_com_error`. Jeśli żaden obiekt `IErrorInfo` nie jest zarejestrowany, zwraca wartość zero.

## <a name="remarks"></a>Uwagi

Wystąpił błąd podczas wywoływania metody `IErrorInfo::GetHelpContext`.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[_com_error, klasa](../cpp/com-error-class.md)
