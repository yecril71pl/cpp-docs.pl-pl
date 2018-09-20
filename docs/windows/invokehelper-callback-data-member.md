---
title: InvokeHelper::callback_, składowa danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::InvokeHelper::callback_
dev_langs:
- C++
helpviewer_keywords:
- callback_ data member
ms.assetid: 6f0cbf6d-0448-46f8-ba71-bd6fd8702e3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8431b8b81cd0761419fa97ad6fd640649893d937
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435847"
---
# <a name="invokehelpercallback-data-member"></a>InvokeHelper::callback_ — Członek danych

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
TCallback callback_;
```

## <a name="remarks"></a>Uwagi

Reprezentuje program obsługi zdarzeń do wywołania po wystąpieniu zdarzenia.

`TCallback` Parametr szablonu określa typ programu obsługi zdarzeń.

## <a name="requirements"></a>Wymagania

**Nagłówek:** event.h

**Namespace:** Microsoft::wrl:: details

## <a name="see-also"></a>Zobacz też

[InvokeHelper, struktura](../windows/invokehelper-structure.md)<br/>
[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)