---
title: _com_error::Source
ms.date: 11/04/2016
f1_keywords:
- _com_error::Source
helpviewer_keywords:
- Source method [C++]
ms.assetid: 55353741-fabc-4b0c-9787-b5a69bb189f2
ms.openlocfilehash: 43dd21297ddd54863d535402dddd59243d589eec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180527"
---
# <a name="_com_errorsource"></a>_com_error::Source

**Specyficzne dla firmy Microsoft**

Wywołuje funkcję `IErrorInfo::GetSource`.

## <a name="syntax"></a>Składnia

```
_bstr_t Source() const;
```

## <a name="return-value"></a>Wartość zwracana

Zwraca wynik `IErrorInfo::GetSource` dla obiektu `IErrorInfo` zarejestrowanego w obiekcie `_com_error`. Powstające `BSTR` są hermetyzowane w obiekcie `_bstr_t`. Jeśli żadna `IErrorInfo` nie jest zarejestrowana, zwraca pustą `_bstr_t`.

## <a name="remarks"></a>Uwagi

Wystąpił błąd podczas wywoływania metody `IErrorInfo::GetSource`.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[_com_error, klasa](../cpp/com-error-class.md)
