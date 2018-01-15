---
title: "Module::releasenotifier — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Module::ReleaseNotifier
dev_langs: C++
helpviewer_keywords: ReleaseNotifier class
ms.assetid: 17249cd1-4d88-42e3-8146-da9e942d12bd
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eb640f146109363a8025818b3ec560c250029914
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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