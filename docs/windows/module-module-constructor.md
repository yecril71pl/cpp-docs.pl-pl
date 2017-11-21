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
ms.openlocfilehash: 33d8d31a7f605fb22e3ca925d53b22b3034c0a7b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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