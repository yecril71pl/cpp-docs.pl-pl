---
title: Module::module — Konstruktor | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::Module
dev_langs:
- C++
helpviewer_keywords:
- Module, constructor
ms.assetid: 5436fc74-61dc-41b6-81af-4f03177159aa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b31e9f1e4536bc124bba359ece10217ef8b7f253
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
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