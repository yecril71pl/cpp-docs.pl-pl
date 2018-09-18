---
title: _com_error::opis | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::Description
dev_langs:
- C++
helpviewer_keywords:
- Description method [C++]
ms.assetid: 88191e24-4ee8-44a6-8c4c-3758e22e0548
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 90208866ee08d6990d8f1b5322a38fbd2d63a651
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091793"
---
# <a name="comerrordescription"></a>_com_error::Description

**Microsoft Specific**

Wywołania `IErrorInfo::GetDescription` funkcji.

## <a name="syntax"></a>Składnia

```
_bstr_t Description( ) const;
```

## <a name="return-value"></a>Wartość zwracana

Zwraca wynik `IErrorInfo::GetDescription` dla `IErrorInfo` obiektu rejestrować się w ramach `_com_error` obiektu. Wartość wynikowa `BSTR` jest hermetyzowany w `_bstr_t` obiektu. Jeśli nie `IErrorInfo` jest rejestrowane, zwraca pustą `_bstr_t`.

## <a name="remarks"></a>Uwagi

Wywołania `IErrorInfo::GetDescription` funkcji i pobiera `IErrorInfo` zarejestrowanych w ramach `_com_error` obiektu. Jakiekolwiek niepowodzenie podczas wywoływania `IErrorInfo::GetDescription` metody jest ignorowana.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[_com_error, klasa](../cpp/com-error-class.md)