---
title: Module::RegisterCOMObject — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::RegisterCOMObject
dev_langs:
- C++
helpviewer_keywords:
- RegisterCOMObject method
ms.assetid: 59f223dc-03c6-429d-95da-b74b3f73b702
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c002dd64049006c8ee74c709c585a3a9d0f253a5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="moduleregistercomobject-method"></a>Module::RegisterCOMObject — Metoda
Rejestruje jednego lub większej liczby obiektów COM, więc inne aplikacje mogą łączyć się z nimi.  
  
## <a name="syntax"></a>Składnia  
  
```  
WRL_NOTHROW virtual HRESULT RegisterCOMObject(  
   const wchar_t* serverName,  
   IID* clsids,  
   IClassFactory** factories,  
   DWORD* cookies,  
   unsigned int count);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `serverName`  
 Pełna nazwa serwera.  
  
 `clsids`  
 Tablica CLSID do zarejestrowania.  
  
 `factories`  
 Tablica IUnknown interfejsów obiektów klas, w których dostępności jest publikowana.  
  
 `cookies`  
 Po zakończeniu operacji tablicy wskaźników do wartości, które identyfikują klasę obiektów, które zostały zarejestrowane. Te wartości są później używane odwołać rejestracji.  
  
 `count`  
 Liczba CLSID do zarejestrowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK Jeśli successfu; w przeciwnym razie wartość HRESULT, takich jak CO_E_OBJISREG, która wskazuje przyczynę działanie nie powiodło się.  
  
## <a name="remarks"></a>Uwagi  
 Obiekty COM są zarejestrowane w usłudze modułu wyliczającego CLSCTX_LOCAL_SERVER CLSCTX wyliczenia.  
  
 Typ połączenia do zarejestrowanych obiektów jest określany przy użyciu kombinacji bieżącego `comflag` parametr szablonu i modułu wyliczającego REGCLS_SUSPENDED REGCLS wyliczenia.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl —
 
 ## <a name="see-also"></a>Zobacz też
 [Klasa modułu](../windows/module-class.md)