---
title: _com_error::Source
ms.date: 11/04/2016
f1_keywords:
- _com_error::Source
helpviewer_keywords:
- Source method [C++]
ms.assetid: 55353741-fabc-4b0c-9787-b5a69bb189f2
ms.openlocfilehash: 682070877f269967405677d027b20707c8366f61
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154964"
---
# <a name="comerrorsource"></a>_com_error::Source

**Microsoft Specific**

Wywołania `IErrorInfo::GetSource` funkcji.

## <a name="syntax"></a>Składnia

```
_bstr_t Source() const;
```

## <a name="return-value"></a>Wartość zwracana

Zwraca wynik `IErrorInfo::GetSource` dla `IErrorInfo` obiektu rejestrować się w ramach `_com_error` obiektu. Wartość wynikowa `BSTR` jest hermetyzowany w `_bstr_t` obiektu. Jeśli nie `IErrorInfo` jest rejestrowane, zwraca pustą `_bstr_t`.

## <a name="remarks"></a>Uwagi

Jakiekolwiek niepowodzenie podczas wywoływania `IErrorInfo::GetSource` metody jest ignorowana.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[_com_error, klasa](../cpp/com-error-class.md)