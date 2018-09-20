---
title: HStringReference::CopyTo, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 179d9b14-1ced-4b16-b297-19ca1e92a462
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 61474e3891def73114f8efc101e1132d5d2593b1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402736"
---
# <a name="hstringreferencecopyto-method"></a>HStringReference::CopyTo — Metoda

Kopiuje bieżący **HStringReference** obiektu do obiektu HSTRING.

## <a name="syntax"></a>Składnia

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>Parametry

*str*<br/>
HSTRING, który otrzymuje kopię.

## <a name="remarks"></a>Uwagi

Ta metoda wywołuje [WindowsDuplicateString](https://msdn.microsoft.com/library/br224634.aspx) funkcji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="see-also"></a>Zobacz też

[HStringReference, klasa](../windows/hstringreference-class.md)