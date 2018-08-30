---
title: Agregacja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- aggregation [C++]
- aggregate objects [C++]
ms.assetid: 7125bb8e-b269-4b50-9bba-295b467a54cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 83d19e53b50791255b87cfa73a51761e2cdf5e1f
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43196148"
---
# <a name="aggregation"></a>Agregacji
Istnieją terminy, gdy obiekt implementujący chcesz korzystać z usług oferowanych przez inną, wstępnie utworzonym obiekt. Ponadto chcesz ten drugi obiekt do są wyświetlane jako fizyczną część pierwsza. COM osiąga obu tych celów poprzez zawierania i agregacji.  
  
 Agregacja oznacza, że zawierającego go obiektu (zewnętrznego) tworzy zawartego w nim obiektu (wewnętrzny) w ramach procesu tworzenia i interfejsy obiekt wewnętrzny są udostępniane przez zewnętrzny. Obiekt umożliwia sam można było agregować, czy nie. Jeśli tak jest, należy go wykonać niektóre zasady w celu agregacji zapewnić prawidłowe działanie.  
  
 Przede wszystkim wszystkie `IUnknown` wywołania metody na przechowywany obiekt musi delegować do obiektu zawierającego.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do modelu COM](../atl/introduction-to-com.md)   
 [Ponowne używanie obiektów](/windows/desktop/com/reusing-objects)

