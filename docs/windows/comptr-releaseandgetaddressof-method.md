---
title: ComPtr::ReleaseAndGetAddressOf, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::ReleaseAndGetAddressOf
dev_langs:
- C++
helpviewer_keywords:
- ReleaseAndGetAddressOf method
ms.assetid: 3751dcb4-d50e-432c-89e4-e736be34d434
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e3efdce7cde39431a8d6f097aace2ed2f5a66b4d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42589950"
---
# <a name="comptrreleaseandgetaddressof-method"></a>ComPtr::ReleaseAndGetAddressOf — Metoda

Zwalnia interfejs skojarzony z tym **ComPtr** i następnie pobiera adres [ptr_ — element](../windows/comptr-ptr-data-member.md) element członkowski danych, który zawiera wskaźnik do interfejsu, który został wydany.

## <a name="syntax"></a>Składnia

```cpp
T** ReleaseAndGetAddressOf();
```

## <a name="return-value"></a>Wartość zwracana

Adres [ptr_ — element](../windows/comptr-ptr-data-member.md) to element członkowski danych **ComPtr**.

## <a name="requirements"></a>Wymagania

**Nagłówek:** client.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[ComPtr, klasa](../windows/comptr-class.md)  
[ComPtr::ptr_, składowa danych](../windows/comptr-ptr-data-member.md)