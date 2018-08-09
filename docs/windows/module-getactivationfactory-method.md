---
title: Module::GetActivationFactory, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GetActivationFactory
dev_langs:
- C++
helpviewer_keywords:
- GetActivationFactory method
ms.assetid: 59da8844-072e-414b-b89c-1db1cc4fd81d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f6fda1c514b6cb3e60a55d35323bf8b116f850ac
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40011871"
---
# <a name="modulegetactivationfactory-method"></a>Module::GetActivationFactory — Metoda
Pobiera fabrykę aktywacji dla modułu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
WRL_NOTHROW HRESULT GetActivationFactory(  
   _In_ HSTRING pActivatibleClassId,  
   _Deref_out_ IActivationFactory **ppIFactory,  
   wchar_t* serverName = nullptr  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *pActivatibleClassId*  
 IID klasy środowiska uruchomieniowego.  
  
 *ppIFactory*  
 IActivationFactory dla klasy określonego środowiska uruchomieniowego.  
  
 *serverName*  
 Nazwa podzbiór fabryki klas w bieżącego modułu. Określ nazwę serwera, używane w [ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md) makro, lub określ **nullptr** można pobrać domyślną nazwę serwera.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wynik HRESULT zwracane przez getactivationfactory —.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa modułu](../windows/module-class.md)  
 [Makra ActivatableClass](../windows/activatableclass-macros.md)