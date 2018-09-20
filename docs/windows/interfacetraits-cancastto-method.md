---
title: InterfaceTraits::CanCastTo, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits::CanCastTo
dev_langs:
- C++
helpviewer_keywords:
- CanCastTo method
ms.assetid: 275847cb-69ea-42bf-910f-05ba6ef8b48d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 705b495e3f6d626a742fd1a63989c8cc658446a4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46379670"
---
# <a name="interfacetraitscancastto-method"></a>InterfaceTraits::CanCastTo — Metoda

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
template<typename T>
static __forceinline bool CanCastTo(
   _In_ T* ptr,
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
Nazwa wskaźnika do typu.

*Parametr riid*<br/>
Identyfikator interfejsu `Base`.

*ppv*<br/>
Jeśli operacja zakończy się pomyślnie, *ppv* wskazuje interfejs określony przez `Base`. W przeciwnym razie *ppv* ustawiono **nullptr**.

## <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli operacja zakończy się pomyślnie i *ptr* jest rzutowany na wskaźnik do `Base`; w przeciwnym razie **false** .

## <a name="remarks"></a>Uwagi

Wskazuje, czy określony wskaźnik może być rzutowany na wskaźnik do `Base`.

Aby uzyskać więcej informacji na temat `Base`, zobacz **publiczne definicje typów** sekcji [interfacetraits — struktura](../windows/interfacetraits-structure.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::wrl:: details

## <a name="see-also"></a>Zobacz też

[InterfaceTraits, struktura](../windows/interfacetraits-structure.md)<br/>
[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)