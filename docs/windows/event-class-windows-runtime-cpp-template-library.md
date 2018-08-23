---
title: Event — klasa (Biblioteka szablonów języka C++ środowiska wykonawczego Windows) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Event
dev_langs:
- C++
ms.assetid: 55dfc9fc-62d4-4bb2-9d85-5b6dd88569e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b40e9c5e04c21cdbcc56581e02751edc84e4617d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606292"
---
# <a name="event-class-windows-runtime-c-template-library"></a>Event — Klasa (Biblioteka szablonów języka C++ środowiska wykonawczego systemu Windows)

Przedstawia zdarzenie.

## <a name="syntax"></a>Składnia

```cpp
class Event : public HandleT<HandleTraits::EventTraits>;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Event::Event Constructor (Biblioteka szablonów języka C++ środowiska uruchomieniowego systemu Windows)](../windows/event-event-constructor-windows-runtime-cpp-template-library.md)|Inicjuje nowe wystąpienie klasy **zdarzeń** klasy.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Operator Event::operator=](../windows/event-operator-assign-operator.md)|Przypisuje określonego **zdarzeń** referencję do bieżącego **zdarzeń** wystąpienia.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`HandleT`

`Event`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Wrappers, przestrzeń nazw](../windows/microsoft-wrl-wrappers-namespace.md)