---
title: Module::module, Konstruktor | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 207b1006aeb57d9c16c09f5d8101a7f64b2cb85b
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39608722"
---
# <a name="modulemodule-constructor"></a>Module::Module — Konstruktor
Inicjuje nowe wystąpienie klasy **modułu** klasy.  
  
## <a name="syntax"></a>Składnia  
  
```  
Module();  
```  
  
## <a name="remarks"></a>Uwagi  
 Ten konstruktor jest chroniona i nie może zostać wywołany z **nowe** — słowo kluczowe. Zamiast tego należy wywołać albo [Module::GetModule, Metoda](../windows/module-getmodule-method.md) lub [Module::Create, Metoda](../windows/module-create-method.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::WRL
 
 ## <a name="see-also"></a>Zobacz też
 [Klasa modułu](../windows/module-class.md)