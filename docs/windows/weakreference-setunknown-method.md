---
title: WeakReference::SetUnknown, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::SetUnknown
dev_langs:
- C++
helpviewer_keywords:
- SetUnknown method
ms.assetid: 5dddb9e3-a7c1-4195-8166-97c5ab6e972f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6fc7accbad5633bd57d7fceb16f82edb82d80f4e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422496"
---
# <a name="weakreferencesetunknown-method"></a>WeakReference::SetUnknown — Metoda

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
void SetUnknown(
   _In_ IUnknown* unk
);
```

### <a name="parameters"></a>Parametry

*UNK*<br/>
Wskaźnik do `IUnknown` interfejs obiektu.

## <a name="remarks"></a>Uwagi

Ustawia silne odwołanie bieżącego **WeakReference** obiekt określony wskaźnik interfejsu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::wrl:: details

## <a name="see-also"></a>Zobacz też

[Weakreference — klasa](../windows/weakreference-class1.md)<br/>
[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)