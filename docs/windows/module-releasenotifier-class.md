---
title: Module::releasenotifier — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::ReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- ReleaseNotifier class
ms.assetid: 17249cd1-4d88-42e3-8146-da9e942d12bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 76edb403fae12dd8b6221d8bd6ec82424bc5a4f7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="modulereleasenotifier-class"></a>Module::ReleaseNotifier — Klasa
Wywołuje program obsługi zdarzeń po zwolnieniu ostatni obiekt w module.  
  
## <a name="syntax"></a>Składnia  
  
```  
class ReleaseNotifier;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Module::ReleaseNotifier::~ReleaseNotifier, destruktor](../windows/module-releasenotifier-tilde-releasenotifier-destructor.md)|Deinitializes bieżące wystąpienie klasy Module::ReleaseNotifier.|  
|[Module::ReleaseNotifier::ReleaseNotifier, konstruktor](../windows/module-releasenotifier-releasenotifier-constructor.md)|Inicjuje nowe wystąpienie klasy Module::ReleaseNotifier.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Module::ReleaseNotifier::Invoke, metoda](../windows/module-releasenotifier-invoke-method.md)|Po zaimplementowaniu, wywołuje program obsługi zdarzeń po zwolnieniu ostatni obiekt w module.|  
|[Module::ReleaseNotifier::Release](../windows/module-releasenotifier-release.md)|Usuwa bieżący obiekt Module::ReleaseNotifier, jeśli obiekt został skonstruowany przy parametr `true`.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `ReleaseNotifier`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl —
 
 ## <a name="see-also"></a>Zobacz też
 [Klasa modułu](../windows/module-class.md)