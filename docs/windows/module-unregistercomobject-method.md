---
title: Module::UnregisterCOMObject, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::UnregisterCOMObject
dev_langs:
- C++
helpviewer_keywords:
- UnregisterCOMObject method
ms.assetid: 5d377525-0385-482a-a215-6e8a1f032861
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3409e0e2c1cac5f3934902523edd2653839989ed
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42575761"
---
# <a name="moduleunregistercomobject-method"></a>Module::UnregisterCOMObject — Metoda

Wyrejestrowuje jeden lub więcej obiektów COM, co uniemożliwia innych aplikacji na połączenie z nich.

## <a name="syntax"></a>Składnia

```cpp
virtual HRESULT UnregisterCOMObject(
   const wchar_t* serverName,
   DWORD* cookies,
   unsigned int count
```

### <a name="parameters"></a>Parametry

*serverName*  
(Nieużywane)

*Pliki cookie*  
Tablica wskaźników do wartości, które identyfikują obiektów klasy do wyrejestrowania. Tablica został utworzony przez [registercomobject —](../windows/module-registercomobject-method.md) metody.

*Liczba*  
Liczba klasy, aby wyrejestrować.

## <a name="return-value"></a>Wartość zwracana

S_OK, jeśli operacja się powiedzie; w przeciwnym razie błąd HRESULT, która wskazuje przyczynę operacja nie powiodła się.

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też
[Klasa modułu](../windows/module-class.md)