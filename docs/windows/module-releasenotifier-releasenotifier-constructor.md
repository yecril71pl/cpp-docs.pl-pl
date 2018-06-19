---
title: 'Module::releasenotifier:: releasenotifier — Konstruktor | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: bbf21e1abc88c0fac0b9d20653fdb45c3706466d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33882472"
---
# <a name="modulereleasenotifierreleasenotifier-constructor"></a>Module::ReleaseNotifier::ReleaseNotifier — Konstruktor
Inicjuje nowe wystąpienie klasy Module::ReleaseNotifier.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
ReleaseNotifier(bool release) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `release`  
 `true` Aby usunąć to wystąpienie, gdy wywoływana jest metoda wersji; `false` nie usuwać tego wystąpienia.  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Module::ReleaseNotifier, klasa](../windows/module-releasenotifier-class.md)