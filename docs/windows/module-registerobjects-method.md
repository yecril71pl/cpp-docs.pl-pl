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
ms.openlocfilehash: 8c9a44fed853fe2f4dcd3196e926b3848566ab4e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597029"
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

*Moduł*  
Tablica obiektów COM i środowiska wykonawczego Windows.

*serverName*  
Nazwa serwera, na którym są tworzone obiekty.

## <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje przyczynę operacja nie powiodła się.

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[Klasa modułu](../windows/module-class.md)