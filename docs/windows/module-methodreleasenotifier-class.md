---
title: Module::MethodReleaseNotifier, klasa | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 80b2653128415cfd847db5b9592df116ffd0d470
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014315"
---
# <a name="modulemethodreleasenotifier-class"></a>Module::MethodReleaseNotifier — Klasa
Wywołuje program obsługi zdarzeń po udostępnieniu ostatni obiekt w bieżącego modułu. Program obsługi zdarzeń jest określona przez obiekt i jego elementów członkowskich wskaźnika do metody.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
template<typename T>  
class MethodReleaseNotifier : public ReleaseNotifier;  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Typ obiektu, którego funkcja członkowska jest program obsługi zdarzeń.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Module::MethodReleaseNotifier::MethodReleaseNotifier, konstruktor](../windows/module-methodreleasenotifier-methodreleasenotifier-constructor.md)|Inicjuje nowe wystąpienie klasy **Module::MethodReleaseNotifier** klasy.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Module::MethodReleaseNotifier::Invoke, metoda](../windows/module-methodreleasenotifier-invoke-method.md)|Wywołuje program obsługi zdarzeń skojarzonych z bieżącym **Module::MethodReleaseNotifier** obiektu.|  
  
### <a name="protected-data-members"></a>Chronione elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Module::MethodReleaseNotifier::method_, składowa danych](../windows/module-methodreleasenotifier-method-data-member.md)|Przechowuje wskaźnik do narzędzia obsługi zdarzeń dla bieżącego **Module::MethodReleaseNotifier** obiektu.|  
|[Module::MethodReleaseNotifier::object_, składowa danych](../windows/module-methodreleasenotifier-object-data-member.md)|Przechowuje wskaźnik do obiektu, którego funkcja członkowska jest program obsługi zdarzeń dla bieżącego **Module::MethodReleaseNotifier** obiektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `ReleaseNotifier`  
  
 `MethodReleaseNotifier`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::WRL
 
 ## <a name="see-also"></a>Zobacz też
 [Klasa modułu](../windows/module-class.md)