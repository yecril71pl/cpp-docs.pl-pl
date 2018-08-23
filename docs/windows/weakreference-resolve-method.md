---
title: Weakreference::Resolve — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::Resolve
dev_langs:
- C++
helpviewer_keywords:
- Resolve method
ms.assetid: fc65a4b7-48a0-4d64-a793-37f566fdd8e7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 59e748ef68d78f9cb77eb335f5c5cd44e058f0d4
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601159"
---
# <a name="weakreferenceresolve-method"></a>WeakReference::Resolve — Metoda

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
STDMETHOD(Resolve)  
   (REFIID riid,
   _Deref_out_opt_ IInspectable **ppvObject
);
```

### <a name="parameters"></a>Parametry

*Parametr riid*  
Identyfikator interfejsu.

*ppvObject*  
Gdy ta operacja zostanie ukończone, kopię bieżącego silne odwołanie, jeśli liczba silne odwołanie jest różna od zera.

## <a name="return-value"></a>Wartość zwracana

- S_OK, jeśli operacja zakończy się pomyślnie, a liczba silne odwołanie ma wartość zero. *PpvObject* parametr ma wartość **nullptr**.

- S_OK, jeśli operacja zakończy się pomyślnie, a liczba silne odwołanie jest różna od zera. *PpvObject* parametr ma wartość silne odwołanie.

- W przeciwnym razie wartość HRESULT, która wskazuje przyczynę tej operacji nie powiodło się.

## <a name="remarks"></a>Uwagi

Ustawia określony wskaźnik do bieżącej wartości silne odwołanie, jeśli liczba silne odwołanie jest różna od zera.

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::wrl:: details

## <a name="see-also"></a>Zobacz też

[WeakReference, klasa1](../windows/weakreference-class1.md)  
[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)