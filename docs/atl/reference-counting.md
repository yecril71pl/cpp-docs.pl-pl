---
title: Zliczanie (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- AddRef method [C++], reference counting
- reference counting
- AddRef method [C++]
- reference counts
- references, counting
ms.assetid: b1fd4514-6de6-429f-9e60-2777c0d07a3d
ms.openlocfilehash: fa160cb40af632321e1b14fd3ca88a4dd578b972
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57293436"
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

## <a name="see-also"></a>Zobacz także

[Wprowadzenie do modelu COM](../atl/introduction-to-com.md)<br/>
[Zarządzanie czasów istnienia obiektów za pomocą zliczanie odwołań](/windows/desktop/com/managing-object-lifetimes-through-reference-counting)
