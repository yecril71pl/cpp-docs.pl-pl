---
title: "Module::releasenotifier:: releasenotifier — Konstruktor | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier
dev_langs: C++
helpviewer_keywords: ReleaseNotifier, constructor
ms.assetid: 889a3c9a-2366-44a1-ba7d-a59c1885e7f3
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a82f8d2f753325c123d78cacbb10fdc25449fd51
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="modulereleasenotifierreleasenotifier-constructor"></a>Module::ReleaseNotifier::ReleaseNotifier — Konstruktor
Inicjuje nowe wystąpienie klasy Module::ReleaseNotifier.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
ReleaseNotifier(bool release) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `release`  
 `true`Aby usunąć to wystąpienie, gdy wywoływana jest metoda wersji; `false` nie usuwać tego wystąpienia.  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Module::releasenotifier — klasa](../windows/module-releasenotifier-class.md)