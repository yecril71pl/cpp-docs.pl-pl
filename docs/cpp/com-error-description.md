---
title: _com_error::Description
ms.date: 11/04/2016
f1_keywords:
- _com_error::Description
helpviewer_keywords:
- Description method [C++]
ms.assetid: 88191e24-4ee8-44a6-8c4c-3758e22e0548
ms.openlocfilehash: de2275f096fe2fde96e64cbc3034602a1fde5e88
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180774"
---
# <a name="_com_errordescription"></a>_com_error::Description

**Specyficzne dla firmy Microsoft**

Wywołuje funkcję `IErrorInfo::GetDescription`.

## <a name="syntax"></a>Składnia

```
_bstr_t Description( ) const;
```

## <a name="return-value"></a>Wartość zwracana

Zwraca wynik `IErrorInfo::GetDescription` dla obiektu `IErrorInfo` zarejestrowanego w obiekcie `_com_error`. Powstające `BSTR` są hermetyzowane w obiekcie `_bstr_t`. Jeśli żadna `IErrorInfo` nie jest zarejestrowana, zwraca pustą `_bstr_t`.

## <a name="remarks"></a>Uwagi

Wywołuje funkcję `IErrorInfo::GetDescription` i pobiera `IErrorInfo` zarejestrowany w obiekcie `_com_error`. Wystąpił błąd podczas wywoływania metody `IErrorInfo::GetDescription`.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[_com_error, klasa](../cpp/com-error-class.md)
