---
title: auto_gcroot — Klasa
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msclr::auto_gcroot
- msclr.auto_gcroot
- auto_gcroot
helpviewer_keywords:
- auto_gcroot
ms.assetid: b5790912-265d-463e-a486-47302e91042a
ms.openlocfilehash: cb89035d928b251c9cc0427612ce6853a96456a9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534241"
---
# <a name="autogcroot-class"></a>auto_gcroot — Klasa

Zarządzanie zasobami automatyczne (takich jak [auto_ptr — klasa](../standard-library/auto-ptr-class.md)) który może służyć do osadzania wirtualnego dojścia do typu macierzystego.

## <a name="syntax"></a>Składnia

```cpp
template<typename _element_type>
class auto_gcroot;
```

#### <a name="parameters"></a>Parametry

*_element_type*<br/>
Typ zarządzany, które można osadzać.

## <a name="requirements"></a>Wymagania

**Plik nagłówkowy** \<msclr\auto_gcroot.h >

**Namespace** msclr

## <a name="see-also"></a>Zobacz też

[auto_gcroot](../dotnet/auto-gcroot.md)<br/>
[auto_gcroot, składowe](../dotnet/auto-gcroot-members.md)<br/>
[Instrukcje: deklarowanie dojść w typach natywnych](../dotnet/how-to-declare-handles-in-native-types.md)<br/>
[auto_handle, klasa](../dotnet/auto-handle-class.md)