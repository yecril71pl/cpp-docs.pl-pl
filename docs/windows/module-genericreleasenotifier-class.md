---
title: Module::GenericReleaseNotifier, klasa | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: ba92e459ffb26ffc1bbb9239a843d628e7041d6d
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40013522"
---
# <a name="modulegenericreleasenotifier-class"></a>Module::GenericReleaseNotifier — Klasa
Wywołuje program obsługi zdarzeń po udostępnieniu ostatni obiekt w bieżącego modułu. Program obsługi zdarzeń jest określone w lambda, funktor lub wskaźnik do funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
template<typename T>  
class GenericReleaseNotifier : public ReleaseNotifier;  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Typ składowej danych, która zawiera lokalizację programu obsługi zdarzeń.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier::GenericReleaseNotifier, konstruktor](../windows/module-genericreleasenotifier-genericreleasenotifier-constructor.md)|Inicjuje nowe wystąpienie klasy **Module::GenericReleaseNotifier** klasy.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier::Invoke, metoda](../windows/module-genericreleasenotifier-invoke-method.md)|Wywołuje program obsługi zdarzeń skojarzonych z bieżącym **Module::GenericReleaseNotifier** obiektu.|  
  
### <a name="protected-data-members"></a>Chronione elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier::callback_, składowa danych](../windows/module-genericreleasenotifier-callback-data-member.md)|Zawiera wyrażenie lambda, funktor lub obsługi zdarzeń wskaźnika do funkcji skojarzony z bieżącym **Module::GenericReleaseNotifier** obiektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `ReleaseNotifier`  
  
 `GenericReleaseNotifier`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::WRL
 
 ## <a name="see-also"></a>Zobacz też
 [Klasa modułu](../windows/module-class.md)