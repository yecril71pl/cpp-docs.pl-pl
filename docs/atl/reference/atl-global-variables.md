---
title: Zmienne globalne ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/06/2017
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATLBASE/_pAtlModule
dev_langs:
- C++
helpviewer_keywords:
- global variables, ATL
- _pAtlModule
ms.assetid: e881a319-99ca-4f5d-8a0b-34b3dcd0f37f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3f32ff38008e55e656bf8901541ffc5ec7246bed
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085995"
---
# <a name="atl-global-variables"></a>Zmienne globalne ATL

## <a name="patlmodule"></a>_pAtlModule

Zmienna globalna przechowywania wskaźnik do bieżącego modułu.  

```cpp
__declspec(selectany) CAtlModule * _pAtlModule
```

### <a name="remarks"></a>Uwagi

Metody dla tej zmiennej globalnej może służyć do zapewnienia funkcji, które (teraz przestarzały) Klasa CComModule udostępnione w Visual C++ 6.0.

### <a name="example"></a>Przykład

```cpp
LONG lLocks = _pAtlModule->GetLockCount();
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h
