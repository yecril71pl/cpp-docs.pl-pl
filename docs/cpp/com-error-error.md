---
title: _com_error::Error
ms.date: 11/04/2016
f1_keywords:
- _com_error::Error
- Error
helpviewer_keywords:
- Error method [C++]
ms.assetid: b53a15fd-198e-4276-afcd-13439c4807f7
ms.openlocfilehash: 8e2c52d10b15822703329dcea18944773f5784ea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180761"
---
# <a name="_com_errorerror"></a>_com_error::Error

**Specyficzne dla firmy Microsoft**

Pobiera wartość HRESULT przekazaną do konstruktora.

## <a name="syntax"></a>Składnia

```
HRESULT Error( ) const throw( );
```

## <a name="return-value"></a>Wartość zwracana

Nieprzetworzony element HRESULT przeszedł do konstruktora.

## <a name="remarks"></a>Uwagi

Pobiera hermetyzowany element HRESULT w obiekcie `_com_error`.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[_com_error, klasa](../cpp/com-error-class.md)
