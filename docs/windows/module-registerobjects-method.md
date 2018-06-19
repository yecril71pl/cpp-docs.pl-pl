---
title: Module::RegisterObjects — metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 986dcfff49529eedd8d495f4c37e19fa2b6cb8bc
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33875347"
---
# <a name="moduleregisterobjects-method"></a>Module::RegisterObjects — Metoda
Rejestruje obiektów COM lub środowiska wykonawczego systemu Windows, więc inne aplikacje mogą łączyć się z nimi.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT RegisterObjects(  
   ModuleBase* module,   
   const wchar_t* serverName);  
```  
  
#### <a name="parameters"></a>Parametry  
 `module`  
 Tablica obiektów COM i środowiska wykonawczego systemu Windows.  
  
 `serverName`  
 Nazwa serwera, na którym są tworzone obiekty.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje przyczynę działanie nie powiodło się.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl —
 
## <a name="see-also"></a>Zobacz też
[Klasa modułu](../windows/module-class.md)