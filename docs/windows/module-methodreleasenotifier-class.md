---
title: Module::methodreleasenotifier — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::MethodReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- MethodReleaseNotifier class
ms.assetid: 5c2902be-964b-488f-9f1c-adf504995cbc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 217e58f73130922d45f0d303e1e91858e8c2272f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880830"
---
# <a name="modulemethodreleasenotifier-class"></a>Module::MethodReleaseNotifier — Klasa
Wywołuje program obsługi zdarzeń po zwolnieniu ostatni obiekt w bieżącego modułu. Program obsługi zdarzeń jest określona przez obiekt i jego elementów członkowskich wskaźnika do metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename T>  
class MethodReleaseNotifier : public ReleaseNotifier;  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ obiektu, którego funkcja członkowska jest programu obsługi zdarzeń.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Module::MethodReleaseNotifier::MethodReleaseNotifier, konstruktor](../windows/module-methodreleasenotifier-methodreleasenotifier-constructor.md)|Inicjuje nowe wystąpienie klasy Module::MethodReleaseNotifier.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Module::MethodReleaseNotifier::Invoke, metoda](../windows/module-methodreleasenotifier-invoke-method.md)|Wywołuje program obsługi zdarzeń skojarzonych z bieżącym obiektem Module::MethodReleaseNotifier.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Module::MethodReleaseNotifier::method_, składowa danych](../windows/module-methodreleasenotifier-method-data-member.md)|Zawiera wskaźnik do obsługi zdarzeń dla bieżącego obiektu Module::MethodReleaseNotifier.|  
|[Module::MethodReleaseNotifier::object_, składowa danych](../windows/module-methodreleasenotifier-object-data-member.md)|Zawiera wskaźnik do obiektu, którego funkcja członkowska jest program obsługi zdarzeń dla bieżącego obiektu Module::MethodReleaseNotifier.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `ReleaseNotifier`  
  
 `MethodReleaseNotifier`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl —
 
 ## <a name="see-also"></a>Zobacz też
 [Klasa modułu](../windows/module-class.md)