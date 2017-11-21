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
ms.openlocfilehash: b98caeedd99199f7d286a4d8ab12c976fffd073c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="aggregation"></a>Agregacji
Brak razy, gdy osoby wdrażającej obiektu chcesz korzystać z usług oferowanych przez inny, wbudowane obiektu. Ponadto chcesz ten drugi obiekt do są wyświetlane jako fizyczne część pierwszy. COM osiąga obu tych celów poprzez zawierania i agregacji.  
  
 Agregacja oznacza, że obiektu zawierającego (zewnętrznego) tworzy zawartego w nim obiektu (wewnętrzny) jako część procesu tworzenia i interfejsy wewnętrzny obiekt są udostępniane przez zewnętrznego. Obiekt umożliwia siebie jako agregowaniu, czy nie. Jeśli tak jest, musi on wykonaj niektóre zasady w celu agregacji działała poprawnie.  
  
 Przede wszystkim wszystkie **IUnknown** wywołania metody w obiekcie zawartych w niej należy delegować do obiektu zawierającego.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do COM](../atl/introduction-to-com.md)   
 [Ponowne wykorzystywanie obiektów](http://msdn.microsoft.com/library/windows/desktop/ms678443)

