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
ms.openlocfilehash: 760a595274ba7a1901138cc0cceceddf97122725
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32353966"
---
# <a name="aggregation"></a>Agregacji
Brak razy, gdy osoby wdrażającej obiektu chcesz korzystać z usług oferowanych przez inny, wbudowane obiektu. Ponadto chcesz ten drugi obiekt do są wyświetlane jako fizyczne część pierwszy. COM osiąga obu tych celów poprzez zawierania i agregacji.  
  
 Agregacja oznacza, że obiektu zawierającego (zewnętrznego) tworzy zawartego w nim obiektu (wewnętrzny) jako część procesu tworzenia i interfejsy wewnętrzny obiekt są udostępniane przez zewnętrznego. Obiekt umożliwia siebie jako agregowaniu, czy nie. Jeśli tak jest, musi on wykonaj niektóre zasady w celu agregacji działała poprawnie.  
  
 Przede wszystkim wszystkie **IUnknown** wywołania metody w obiekcie zawartych w niej należy delegować do obiektu zawierającego.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do COM](../atl/introduction-to-com.md)   
 [Ponowne wykorzystywanie obiektów](http://msdn.microsoft.com/library/windows/desktop/ms678443)

