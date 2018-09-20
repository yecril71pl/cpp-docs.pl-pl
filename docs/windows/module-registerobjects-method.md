---
title: Module::RegisterObjects, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::RegisterObjects
dev_langs:
- C++
helpviewer_keywords:
- RegisterObjects method
ms.assetid: db4077b7-068d-4534-aaa5-41b5444ccb49
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d332d59ed821e433e0ec1ba025f882b4339ad69a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440904"
---
# <a name="moduleregisterobjects-method"></a>Module::RegisterObjects — Metoda

Rejestruje obiekty COM lub środowiska wykonawczego Windows, dzięki czemu inne aplikacje mogą łączyć się z nimi.

## <a name="syntax"></a>Składnia

```cpp
HRESULT RegisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>Parametry

*Moduł*<br/>
Tablica obiektów COM i środowiska wykonawczego Windows.

*serverName*<br/>
Nazwa serwera, na którym są tworzone obiekty.

## <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje przyczynę operacja nie powiodła się.

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[Klasa modułu](../windows/module-class.md)