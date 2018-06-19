---
title: Zliczanie (ATL) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- AddRef method [C++], reference counting
- reference counting
- AddRef method [C++]
- reference counts
- references, counting
ms.assetid: b1fd4514-6de6-429f-9e60-2777c0d07a3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d1ba27f00bf25f88575101b1299daf50f94000ad
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358251"
---
# <a name="reference-counting"></a>Liczenie odwołań
COM sam nie automatycznie próbuje usunąć obiekt z pamięci po sądzi, że obiekt jest już używany. Zamiast tego obiektu programisty należy usunąć nieużywane obiektu. Programistę Określa, czy obiekt można usunąć zależności od liczby odwołania.  
  
 Używa COM **IUnknown** metod, [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) i [wersji](http://msdn.microsoft.com/library/windows/desktop/ms682317), aby zarządzać liczebności referencyjnej interfejsów dla obiektu. Ogólne zasady do wywoływania metody te są:  
  
-   Zawsze, gdy klient otrzymuje wskaźnika interfejsu `AddRef` musi zostać wywołana w interfejsie.  
  
-   Zawsze, gdy klient zakończy działanie przy użyciu wskaźnika interfejsu, należy wywołać **wersji**.  
  
 W prostych implementacji każdy `AddRef` wywoływać zwiększa i każdego **wersji** wywołać zmniejsza zmienną licznika wewnątrz obiektu. Zwrócona liczba od zera. interfejs już nie ma żadnych użytkowników i może się usunąć z pamięci.  
  
 Liczenie odwołań również można zaimplementować tak, aby jest liczony każdego odwołania do obiektu (nie do określonego interfejsu). W takim przypadku każdy `AddRef` i **wersji** wywołać delegatów centralnej implementacji dla obiektu, i **wersji** zwalnia całego obiektu, gdy jego liczebności referencyjnej osiągnie wartość zero.  
  
> [!NOTE]
>  Gdy `CComObject`— obiekt pochodny jest tworzony przy użyciu **nowe** operatora, liczba odwołań wynosi 0. W związku z tym wywołaniu `AddRef` muszą być wprowadzane po pomyślnym utworzeniu `CComObject`-pochodzi z obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do COM](../atl/introduction-to-com.md)   
 [Zarządzanie okresy istnienia obiektu przez liczenie odwołań](http://msdn.microsoft.com/library/windows/desktop/ms687260)

