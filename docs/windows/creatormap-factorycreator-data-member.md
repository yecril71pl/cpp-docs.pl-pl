---
title: CreatorMap::factoryCreator, składowa danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreatorMap::factoryCreator
dev_langs:
- C++
helpviewer_keywords:
- factoryCreator data member
ms.assetid: c9aac363-8f38-4cfd-9605-1e6ac74c5097
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 12d4fdd415ab37c9af0b0b34651e7cd2f00cf31b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405284"
---
# <a name="creatormapfactorycreator-data-member"></a>CreatorMap::factoryCreator — Członek danych

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
HRESULT (*factoryCreator)(
   unsigned int* currentflags,
   const CreatorMap* entry,
   REFIID iidClassFactory,
IUnknown** factory);
```

### <a name="parameters"></a>Parametry

*currentflags*<br/>
Jedną z [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) modułów wyliczających.

*entry*<br/>
Creatormap —.

*iidClassFactory*<br/>
Identyfikator interfejsu fabrykę klas.

*Fabryka*<br/>
Po zakończeniu tej operacji adres fabrykę klas.

## <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.

## <a name="remarks"></a>Uwagi

Tworzy fabrykę dla określonego creatormap —.

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::wrl:: details

## <a name="see-also"></a>Zobacz też

[CreatorMap, struktura](../windows/creatormap-structure.md)<br/>
[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)