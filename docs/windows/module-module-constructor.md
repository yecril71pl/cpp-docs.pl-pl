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
ms.openlocfilehash: d63b90bb3622129589fca41c029f548a07ec21b8
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017659"
---
# <a name="modulemodule-constructor"></a>Module::Module — Konstruktor
Inicjuje nowe wystąpienie klasy **modułu** klasy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
Module();  
```  
  
## <a name="remarks"></a>Uwagi  
 Ten konstruktor jest chroniona i nie może zostać wywołany z **nowe** — słowo kluczowe. Zamiast tego należy wywołać albo [Module::GetModule, Metoda](../windows/module-getmodule-method.md) lub [Module::Create, Metoda](../windows/module-create-method.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::WRL
 
 ## <a name="see-also"></a>Zobacz też
 [Klasa modułu](../windows/module-class.md)