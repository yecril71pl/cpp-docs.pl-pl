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
ms.openlocfilehash: 8e0ce8b2cc412c576b0eded9662d8e70b34cf2ec
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37850816"
---
# <a name="reference-counting"></a>Zliczanie odwołań
COM, sama nie automatycznie próbuje usunąć obiekt z pamięci, jeśli uważa, że obiekt jest już używany. Zamiast tego programisty obiektu, należy usunąć nieużywane obiektu. Programistę Określa, czy obiekt można usunąć zależności od liczby odwołań.  
  
 COM używa `IUnknown` metod [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) i [wersji](http://msdn.microsoft.com/library/windows/desktop/ms682317), aby zarządzać licznikiem odwołań interfejsów na obiekcie. Ogólne zasady wywoływanie tych metod są:  
  
-   Zawsze, gdy klient odbierze wskaźnika interfejsu `AddRef` musi zostać wywołana w interfejsie.  
  
-   Zawsze, gdy klient zakończy się za pomocą wskaźnika interfejsu, należy wywołać `Release`.  
  
 W prostych implementacji każdy `AddRef` wywołać przyrosty, a każdy `Release` wywołać zmniejsza zmienną licznika wewnątrz obiektu. Gdy liczba zwraca zero, interfejs nie jest już zawiera wszystkich użytkowników i jest bezpłatna usunąć samego z pamięci.  
  
 Zliczanie odwołań może też być implementowany tak, aby każde odwołanie do obiektu (nie do poszczególnych interfejsu) jest liczony. W takim przypadku każdy `AddRef` i `Release` wywoływać delegatów centralnej implementacji dla obiektu i `Release` zwalnia całego obiektu, gdy jego licznik odwołań osiągnie zero.  
  
> [!NOTE]
>  Gdy `CComObject`— pochodnej obiekt jest tworzony przy użyciu **nowe** operatora, licznik odwołań to 0. W związku z tym, wywołanie `AddRef` musi nastąpić po pomyślnym utworzeniu `CComObject`-pochodnych obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do modelu COM](../atl/introduction-to-com.md)   
 [Zarządzanie czasów istnienia obiektów za pomocą zliczanie odwołań](http://msdn.microsoft.com/library/windows/desktop/ms687260)

