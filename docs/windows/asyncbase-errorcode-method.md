---
title: AsyncBase::ErrorCode, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::ErrorCode
dev_langs:
- C++
helpviewer_keywords:
- ErrorCode method
ms.assetid: 3f5f0f69-d60a-4a67-8cc6-a55fdc89a192
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7336824d04745440a1f6152ebacfed2afc62258e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602381"
---
# <a name="asyncbaseerrorcode-method"></a>AsyncBase::ErrorCode — Metoda

Pobiera kod błędu dla bieżącej operacji asynchronicznej.

## <a name="syntax"></a>Składnia

```cpp
inline void ErrorCode(
   HRESULT *error
);
```

### <a name="parameters"></a>Parametry

*Błąd*  
Lokalizacja, w której przechowuje bieżący kod błędu w tej operacji.

## <a name="remarks"></a>Uwagi

Ta operacja jest metodą o bezpiecznych wątkach.

## <a name="requirements"></a>Wymagania

**Nagłówek:** async.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[AsyncBase, klasa](../windows/asyncbase-class.md)