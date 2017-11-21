---
title: "Module::genericreleasenotifier — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Module::GenericReleaseNotifier
dev_langs: C++
helpviewer_keywords: GenericReleaseNotifier class
ms.assetid: 244a8fbe-f89b-409b-aa65-db3e37f9b125
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b753d1eac4de6b7c6684a33889163344dfefe19f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
|[Module::genericreleasenotifier:: genericreleasenotifier — Konstruktor](../windows/module-genericreleasenotifier-genericreleasenotifier-constructor.md)|Inicjuje nowe wystąpienie klasy Module::GenericReleaseNotifier.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier:: Invoke — metoda](../windows/module-genericreleasenotifier-invoke-method.md)|Wywołuje program obsługi zdarzeń skojarzonych z bieżącym obiektem Module::GenericReleaseNotifier.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Module::genericreleasenotifier:: callback_ — członek danych](../windows/module-genericreleasenotifier-callback-data-member.md)|Przechowuje lambda, obiekt lub program obsługi zdarzeń wskaźnika do funkcji skojarzonych z bieżącym obiektem Module::GenericReleaseNotifier.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `ReleaseNotifier`  
  
 `GenericReleaseNotifier`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl —
 
 ## <a name="see-also"></a>Zobacz też
 [Klasa modułu](../windows/module-class.md)