---
title: "Module::genericreleasenotifier — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GenericReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- GenericReleaseNotifier class
ms.assetid: 244a8fbe-f89b-409b-aa65-db3e37f9b125
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c87205d1d52c8273ac7eea55fcc5385810349f1f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="modulegenericreleasenotifier-class"></a>Module::GenericReleaseNotifier — Klasa
Wywołuje program obsługi zdarzeń po zwolnieniu ostatni obiekt w bieżącego modułu. Program obsługi zdarzeń jest określona przez na lambda, obiekt lub wskaźnik do funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<  
   typename T  
>  
class GenericReleaseNotifier : public ReleaseNotifier;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ elementu członkowskiego danych zawiera lokalizację programu obsługi zdarzeń.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier::GenericReleaseNotifier, konstruktor](../windows/module-genericreleasenotifier-genericreleasenotifier-constructor.md)|Inicjuje nowe wystąpienie klasy Module::GenericReleaseNotifier.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier::Invoke, metoda](../windows/module-genericreleasenotifier-invoke-method.md)|Wywołuje program obsługi zdarzeń skojarzonych z bieżącym obiektem Module::GenericReleaseNotifier.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier::callback_, składowa danych](../windows/module-genericreleasenotifier-callback-data-member.md)|Przechowuje lambda, obiekt lub program obsługi zdarzeń wskaźnika do funkcji skojarzonych z bieżącym obiektem Module::GenericReleaseNotifier.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `ReleaseNotifier`  
  
 `GenericReleaseNotifier`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl —
 
 ## <a name="see-also"></a>Zobacz też
 [Klasa modułu](../windows/module-class.md)