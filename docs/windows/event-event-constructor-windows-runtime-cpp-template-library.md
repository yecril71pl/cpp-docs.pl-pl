---
title: Event::Event Constructor (Biblioteka szablonów języka C++ środowiska wykonawczego Windows) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Event::Event
dev_langs:
- C++
ms.assetid: 21495297-9612-4095-9256-16e168cc0021
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a377967ff2fe469f73f993d779b48037d462e6d7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42575888"
---
# <a name="eventevent-constructor-windows-runtime-c-template-library"></a>Event::Event Constructor (Biblioteka szablonów języka C++ środowiska wykonawczego systemu Windows)

Inicjuje nowe wystąpienie klasy **zdarzeń** klasy.

## <a name="syntax"></a>Składnia

```cpp
explicit Event(
   HANDLE h = HandleT::Traits::GetInvalidValue()  
);
WRL_NOTHROW Event(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>Parametry

*h*  
Obsłuż to zdarzenie. Domyślnie *h* jest inicjowany do **nullptr**.

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="see-also"></a>Zobacz też

[Event, klasa (Biblioteka szablonów języka C++ środowiska uruchomieniowego systemu Windows)](../windows/event-class-windows-runtime-cpp-template-library.md)