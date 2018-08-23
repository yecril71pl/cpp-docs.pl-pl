---
title: HString::CopyTo, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: a1fd2ef0-e175-4c18-927b-550e02a89e43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4e2a4ce5a2952a990ee3a2d934d6207656a57376
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592137"
---
# <a name="hstringcopyto-method"></a>HString::CopyTo — Metoda

Kopiuje bieżący **HString** obiektu do obiektu HSTRING.

## <a name="syntax"></a>Składnia

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>Parametry

*str*  
HSTRING, który otrzymuje kopię.

## <a name="remarks"></a>Uwagi

Ta metoda wywołuje [WindowsDuplicateString](http://msdn.microsoft.com/library/br224634.aspx) funkcji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="see-also"></a>Zobacz też

[HString, klasa](../windows/hstring-class.md)