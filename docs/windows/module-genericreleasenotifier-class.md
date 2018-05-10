---
title: Module::genericreleasenotifier — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GenericReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- GenericReleaseNotifier class
ms.assetid: 244a8fbe-f89b-409b-aa65-db3e37f9b125
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c3ba58e08bac36d905fbf874546d7791f2aa3fcb
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="modulegenericreleasenotifier-class"></a>Module::GenericReleaseNotifier — Klasa
Wywołuje program obsługi zdarzeń po zwolnieniu ostatni obiekt w bieżącego modułu. Program obsługi zdarzeń jest określona przez na lambda, obiekt lub wskaźnik do funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename T>  
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