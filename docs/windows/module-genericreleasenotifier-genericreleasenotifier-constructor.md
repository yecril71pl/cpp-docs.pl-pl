---
title: "Module::genericreleasenotifier:: genericreleasenotifier — Konstruktor | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Module::GenericReleaseNotifier::GenericReleaseNotifier
dev_langs: C++
helpviewer_keywords: GenericReleaseNotifier, constructor
ms.assetid: feb5b687-a4b0-4809-9022-8f292181b7a1
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f0309040b64614280d2314daa83c5919514b3fb6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="modulegenericreleasenotifiergenericreleasenotifier-constructor"></a>Module::GenericReleaseNotifier::GenericReleaseNotifier — Konstruktor
Inicjuje nowe wystąpienie klasy Module::GenericReleaseNotifier.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      GenericReleaseNotifier(  
   T callback,   
   bool release  
) throw() : ReleaseNotifier(release), callback_(callback);  
```  
  
#### <a name="parameters"></a>Parametry  
 `callback`  
 Lambda, obiekt lub obsługi zdarzeń wskaźnika do funkcji, która może zostać wywołana z funkcji nawiasów (`()`).  
  
 `release`  
 Określ `true` umożliwia wywołanie odpowiadającego [modułu:: ReleaseNotifier::Release()](../windows/module-releasenotifier-release.md) metody; w przeciwnym razie określ `false`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Module::genericreleasenotifier — klasa](../windows/module-genericreleasenotifier-class.md)