---
title: _com_error::ErrorInfo
ms.date: 11/04/2016
f1_keywords:
- _com_error::ErrorInfo
helpviewer_keywords:
- ErrorInfo method [C++]
ms.assetid: 071b446c-4395-4fb8-bd3d-300a8b25f5cd
ms.openlocfilehash: 59ada8a7e098e57cca5641a439365851bbae2485
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155075"
---
# <a name="comerrorerrorinfo"></a>_com_error::ErrorInfo

**Microsoft Specific**

Pobiera `IErrorInfo` obiekt przekazany do konstruktora.

## <a name="syntax"></a>Składnia

```
IErrorInfo * ErrorInfo( ) const throw( );
```

## <a name="return-value"></a>Wartość zwracana

Nieprzetworzone `IErrorInfo` element przekazany do konstruktora.

## <a name="remarks"></a>Uwagi

Pobiera zhermetyzowany `IErrorInfo` pozycja `_com_error` obiekt lub wartość NULL, jeśli nie `IErrorInfo` elementu są rejestrowane. Obiekt wywołujący musi wywołać `Release` na zwracanym obiekcie po zakończeniu korzystania z niego.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[_com_error, klasa](../cpp/com-error-class.md)