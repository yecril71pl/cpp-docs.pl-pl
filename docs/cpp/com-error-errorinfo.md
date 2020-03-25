---
title: _com_error::ErrorInfo
ms.date: 11/04/2016
f1_keywords:
- _com_error::ErrorInfo
helpviewer_keywords:
- ErrorInfo method [C++]
ms.assetid: 071b446c-4395-4fb8-bd3d-300a8b25f5cd
ms.openlocfilehash: cedb9ccadc63166c43d980333d93a195254700d8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180709"
---
# <a name="_com_errorerrorinfo"></a>_com_error::ErrorInfo

**Specyficzne dla firmy Microsoft**

Pobiera obiekt `IErrorInfo` przekazywać do konstruktora.

## <a name="syntax"></a>Składnia

```
IErrorInfo * ErrorInfo( ) const throw( );
```

## <a name="return-value"></a>Wartość zwracana

Nieprzetworzony element `IErrorInfo` przeszedł do konstruktora.

## <a name="remarks"></a>Uwagi

Pobiera hermetyzowane `IErrorInfo` w obiekcie `_com_error` lub wartość NULL, jeśli żaden `IErrorInfo` element nie jest zarejestrowany. Obiekt wywołujący musi wywołać `Release` na zwróconym obiekcie po zakończeniu jego używania.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[_com_error, klasa](../cpp/com-error-class.md)
