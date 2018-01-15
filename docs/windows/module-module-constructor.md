---
title: "Module::module — Konstruktor | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Module::Module
dev_langs: C++
helpviewer_keywords: Module, constructor
ms.assetid: 5436fc74-61dc-41b6-81af-4f03177159aa
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 24e74bf30f932fa8029c64d27ce55dd2a75a99aa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="modulemodule-constructor"></a>Module::Module — Konstruktor
Inicjuje nowe wystąpienie klasy modułu.  
  
## <a name="syntax"></a>Składnia  
  
```  
Module();  
```  
  
## <a name="remarks"></a>Uwagi  
 Ten konstruktor jest chroniona i nie można wywołać z `new` — słowo kluczowe. Zamiast tego wywołać albo [Module::GetModule — metoda](../windows/module-getmodule-method.md) lub [Module::Create — metoda](../windows/module-create-method.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl —
 
 ## <a name="see-also"></a>Zobacz też
 [Klasa modułu](../windows/module-class.md)