---
title: 'Module::methodreleasenotifier:: methodreleasenotifier — Konstruktor | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- MethodReleaseNotifier, constructor
ms.assetid: 762e2ca4-0a92-49de-9ff5-d3efa0f067c0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 62f136fb9aac184d6ca81314aafea270e7b33a87
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42583874"
---
# <a name="modulemethodreleasenotifiermethodreleasenotifier-constructor"></a>Module::MethodReleaseNotifier::MethodReleaseNotifier — Konstruktor

Inicjuje nowe wystąpienie klasy **Module::MethodReleaseNotifier** klasy.

## <a name="syntax"></a>Składnia

```cpp
MethodReleaseNotifier(
   _In_ T* object,
   _In_ void (T::* method)(),
   bool release) throw() :
            ReleaseNotifier(release), object_(object),
            method_(method);
```

### <a name="parameters"></a>Parametry

*object*  
Obiekt, którego funkcja członkowska jest program obsługi zdarzeń.

*— Metoda*  
Funkcja elementu członkowskiego parametru *obiektu* oznacza to program obsługi zdarzeń.

*Wydania*  
Określ **true** umożliwiające wywołanie bazowego [modułu:: ReleaseNotifier::Release()](../windows/module-releasenotifier-release.md) metody; w przeciwnym razie określ **false**.

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[Module::MethodReleaseNotifier, klasa](../windows/module-methodreleasenotifier-class.md)