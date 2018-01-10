---
title: Agregacja | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- aggregation [C++]
- aggregate objects [C++]
ms.assetid: 7125bb8e-b269-4b50-9bba-295b467a54cc
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8dbb0332bc7e55464e5b8af9d0b57e236f23dc86
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="aggregation"></a>Agregacji
Brak razy, gdy osoby wdrażającej obiektu chcesz korzystać z usług oferowanych przez inny, wbudowane obiektu. Ponadto chcesz ten drugi obiekt do są wyświetlane jako fizyczne część pierwszy. COM osiąga obu tych celów poprzez zawierania i agregacji.  
  
 Agregacja oznacza, że obiektu zawierającego (zewnętrznego) tworzy zawartego w nim obiektu (wewnętrzny) jako część procesu tworzenia i interfejsy wewnętrzny obiekt są udostępniane przez zewnętrznego. Obiekt umożliwia siebie jako agregowaniu, czy nie. Jeśli tak jest, musi on wykonaj niektóre zasady w celu agregacji działała poprawnie.  
  
 Przede wszystkim wszystkie **IUnknown** wywołania metody w obiekcie zawartych w niej należy delegować do obiektu zawierającego.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do COM](../atl/introduction-to-com.md)   
 [Ponowne wykorzystywanie obiektów](http://msdn.microsoft.com/library/windows/desktop/ms678443)

