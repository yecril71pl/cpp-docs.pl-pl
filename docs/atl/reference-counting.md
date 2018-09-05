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
ms.openlocfilehash: e48cea73ede2a7c5ec529f4fc44f917494560ced
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43751149"
---
# <a name="reference-counting"></a>Zliczanie odwołań

COM, sama nie automatycznie próbuje usunąć obiekt z pamięci, jeśli uważa, że obiekt jest już używany. Zamiast tego programisty obiektu, należy usunąć nieużywane obiektu. Programistę Określa, czy obiekt można usunąć zależności od liczby odwołań.

COM używa `IUnknown` metod [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref) i [wersji](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release), aby zarządzać licznikiem odwołań interfejsów na obiekcie. Ogólne zasady wywoływanie tych metod są:

- Zawsze, gdy klient odbierze wskaźnika interfejsu `AddRef` musi zostać wywołana w interfejsie.

- Zawsze, gdy klient zakończy się za pomocą wskaźnika interfejsu, należy wywołać `Release`.

W prostych implementacji każdy `AddRef` wywołać przyrosty, a każdy `Release` wywołać zmniejsza zmienną licznika wewnątrz obiektu. Gdy liczba zwraca zero, interfejs nie jest już zawiera wszystkich użytkowników i jest bezpłatna usunąć samego z pamięci.

Zliczanie odwołań może też być implementowany tak, aby każde odwołanie do obiektu (nie do poszczególnych interfejsu) jest liczony. W takim przypadku każdy `AddRef` i `Release` wywoływać delegatów centralnej implementacji dla obiektu i `Release` zwalnia całego obiektu, gdy jego licznik odwołań osiągnie zero.

> [!NOTE]
>  Gdy `CComObject`— pochodnej obiekt jest tworzony przy użyciu **nowe** operatora, licznik odwołań to 0. W związku z tym, wywołanie `AddRef` musi nastąpić po pomyślnym utworzeniu `CComObject`-pochodnych obiektu.

## <a name="see-also"></a>Zobacz też

[Wprowadzenie do modelu COM](../atl/introduction-to-com.md)   
[Zarządzanie czasów istnienia obiektów za pomocą zliczanie odwołań](/windows/desktop/com/managing-object-lifetimes-through-reference-counting)

