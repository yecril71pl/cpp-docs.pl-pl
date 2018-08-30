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
ms.openlocfilehash: da0e8e241aeb3f0eb5096d64cd63425ca2102fb0
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211174"
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

Ta metoda wywołuje [WindowsDuplicateString](https://msdn.microsoft.com/library/br224634.aspx) funkcji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="see-also"></a>Zobacz też

[HString, klasa](../windows/hstring-class.md)