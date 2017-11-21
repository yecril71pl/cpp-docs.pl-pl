---
title: "Module::GetActivationFactory — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Module::GetActivationFactory
dev_langs: C++
helpviewer_keywords: GetActivationFactory method
ms.assetid: 59da8844-072e-414b-b89c-1db1cc4fd81d
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6c381f523e5318bde308f17266ecd6d33d776e29
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="modulegetactivationfactory-method"></a>Module::GetActivationFactory — Metoda
Pobiera fabryki aktywacji dla modułu.  
  
## <a name="syntax"></a>Składnia  
  
```  
WRL_NOTHROW HRESULT GetActivationFactory(  
   _In_ HSTRING pActivatibleClassId,  
   _Deref_out_ IActivationFactory **ppIFactory,  
   wchar_t* serverName = nullptr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pActivatibleClassId`  
 Identyfikator IID klasy środowiska wykonawczego.  
  
 `ppIFactory`  
 IActivationFactory dla określonego środowiska uruchomieniowego klasy.  
  
 `serverName`  
 Nazwa podzbiór fabryki klas w bieżącego modułu. Określ nazwę serwera, używane w [ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md) makra, lub określ `nullptr` można pobrać domyślnej nazwy serwera.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT zwrócony przez GetActivationFactory.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
[Klasa modułu](../windows/module-class.md) [ActivatableClass makra](../windows/activatableclass-macros.md)