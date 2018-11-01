---
title: _com_error::HelpFile
ms.date: 11/04/2016
f1_keywords:
- _com_error::HelpFile
helpviewer_keywords:
- HelpFile method [C++]
ms.assetid: d2d3a0a1-6b62-4d52-a818-3cfae545a4af
ms.openlocfilehash: 826ac53f001355127f16b7ad2a7583a0f8800de7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50433582"
---
# <a name="comerrorhelpfile"></a>_com_error::HelpFile

**Microsoft Specific**

Wywołania `IErrorInfo::GetHelpFile` funkcji.

## <a name="syntax"></a>Składnia

```
_bstr_t HelpFile() const;
```

## <a name="return-value"></a>Wartość zwracana

Zwraca wynik `IErrorInfo::GetHelpFile` dla `IErrorInfo` obiektu rejestrować się w ramach `_com_error` obiektu. Wynikowy BSTR jest hermetyzowany w `_bstr_t` obiektu. Jeśli nie `IErrorInfo` jest rejestrowane, zwraca pustą `_bstr_t`.

## <a name="remarks"></a>Uwagi

Jakiekolwiek niepowodzenie podczas wywoływania `IErrorInfo::GetHelpFile` metody jest ignorowana.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[_com_error, klasa](../cpp/com-error-class.md)