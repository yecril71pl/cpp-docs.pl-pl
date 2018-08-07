---
title: 'Module::releasenotifier:: releasenotifier, Konstruktor | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- ReleaseNotifier, constructor
ms.assetid: 889a3c9a-2366-44a1-ba7d-a59c1885e7f3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 93dca0500971f0bcfdefd017457e02bf6a033660
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39608472"
---
# <a name="modulereleasenotifierreleasenotifier-constructor"></a>Module::ReleaseNotifier::ReleaseNotifier — Konstruktor
Inicjuje nowe wystąpienie klasy **Module::ReleaseNotifier** klasy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
ReleaseNotifier(bool release) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 *Wydania*  
 **wartość true,** można usunąć to wystąpienie kiedy `Release` wywoływana jest metoda; **false** nie należy usuwać tego wystąpienia.  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [Module::ReleaseNotifier, klasa](../windows/module-releasenotifier-class.md)