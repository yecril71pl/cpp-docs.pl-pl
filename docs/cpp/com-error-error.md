---
title: _com_error::Error
ms.date: 11/04/2016
f1_keywords:
- _com_error::Error
- Error
helpviewer_keywords:
- Error method [C++]
ms.assetid: b53a15fd-198e-4276-afcd-13439c4807f7
ms.openlocfilehash: 606f553060e71ece18b3d48159ec40133be28965
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155101"
---
# <a name="comerrorerror"></a>_com_error::Error

**Microsoft Specific**

Pobiera wartość HRESULT przekazany do konstruktora.

## <a name="syntax"></a>Składnia

```
HRESULT Error( ) const throw( );
```

## <a name="return-value"></a>Wartość zwracana

Nieprzetworzone elementu HRESULT przekazany do konstruktora.

## <a name="remarks"></a>Uwagi

Pobiera element HRESULT hermetyzowany w `_com_error` obiektu.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[_com_error, klasa](../cpp/com-error-class.md)