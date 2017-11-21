---
title: "Module::RegisterObjects — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Module::RegisterObjects
dev_langs: C++
helpviewer_keywords: RegisterObjects method
ms.assetid: db4077b7-068d-4534-aaa5-41b5444ccb49
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fbff1d4c16c8cfb4f265760a6919637808efe28d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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