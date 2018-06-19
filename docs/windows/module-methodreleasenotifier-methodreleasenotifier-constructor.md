---
title: 'Module::methodreleasenotifier:: methodreleasenotifier — Konstruktor | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- MethodReleaseNotifier, constructor
ms.assetid: 762e2ca4-0a92-49de-9ff5-d3efa0f067c0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 91540ca3fff03f1f0a449413c2d1ca72781c70f1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33875230"
---
# <a name="modulemethodreleasenotifiermethodreleasenotifier-constructor"></a>Module::MethodReleaseNotifier::MethodReleaseNotifier — Konstruktor
Inicjuje nowe wystąpienie klasy Module::MethodReleaseNotifier.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
MethodReleaseNotifier(  
   _In_ T* object,   
   _In_ void (T::* method)(),   
   bool release) throw() :  
            ReleaseNotifier(release), object_(object),   
            method_(method);  
```  
  
#### <a name="parameters"></a>Parametry  
 `object`  
 Obiekt, którego funkcja członkowska jest obsługą zdarzeń.  
  
 `method`  
 Funkcja członkowska parametru `object` czyli obsługi zdarzeń.  
  
 `release`  
 Określ `true` umożliwia wywołanie odpowiadającego [modułu:: ReleaseNotifier::Release()](../windows/module-releasenotifier-release.md) metody; w przeciwnym razie określ `false`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Module::MethodReleaseNotifier, klasa](../windows/module-methodreleasenotifier-class.md)