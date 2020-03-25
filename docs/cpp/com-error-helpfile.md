---
title: _com_error::HelpFile
ms.date: 11/04/2016
f1_keywords:
- _com_error::HelpFile
helpviewer_keywords:
- HelpFile method [C++]
ms.assetid: d2d3a0a1-6b62-4d52-a818-3cfae545a4af
ms.openlocfilehash: 775adfa7d5dd5aca098edcd793c2164d65fe7efa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190225"
---
# <a name="_com_errorhelpfile"></a>_com_error::HelpFile

**Specyficzne dla firmy Microsoft**

Wywołuje funkcję `IErrorInfo::GetHelpFile`.

## <a name="syntax"></a>Składnia

```
_bstr_t HelpFile() const;
```

## <a name="return-value"></a>Wartość zwracana

Zwraca wynik `IErrorInfo::GetHelpFile` dla obiektu `IErrorInfo` zarejestrowanego w obiekcie `_com_error`. Powstający element BSTR jest hermetyzowany w obiekcie `_bstr_t`. Jeśli żadna `IErrorInfo` nie jest zarejestrowana, zwraca pustą `_bstr_t`.

## <a name="remarks"></a>Uwagi

Wystąpił błąd podczas wywoływania metody `IErrorInfo::GetHelpFile`.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[_com_error, klasa](../cpp/com-error-class.md)
