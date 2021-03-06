---
title: Zliczanie odwołań (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- AddRef method [C++], reference counting
- reference counting
- AddRef method [C++]
- reference counts
- references, counting
ms.assetid: b1fd4514-6de6-429f-9e60-2777c0d07a3d
ms.openlocfilehash: f90c818e58ae7ef6e4a0b771cb53ae5b185d1617
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224347"
---
# <a name="reference-counting"></a>Zliczanie odwołań

Sam COM nie próbuje automatycznie usunąć obiektu z pamięci, gdy uzna, że obiekt nie jest już używany. Zamiast tego programista obiektu musi usunąć nieużywany obiekt. Programista określa, czy obiekt może zostać usunięty na podstawie liczby odwołań.

COM używa `IUnknown` metod, [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) i [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release), aby zarządzać liczbą odwołań interfejsów w obiekcie. Ogólne reguły wywołania tych metod są następujące:

- Za każdym razem, gdy klient otrzymuje wskaźnik interfejsu, `AddRef` musi zostać wywołany w interfejsie.

- Za każdym razem, gdy klient zakończył korzystanie z wskaźnika interfejsu, musi wywołać `Release` .

W prostej implementacji każda wartość `AddRef` przyrostu wywołań i każde `Release` wywołanie zmniejsza zmienną licznika wewnątrz obiektu. Gdy liczba zwraca wartość zero, interfejs nie ma już żadnych użytkowników i jest bezpłatny do usuwania z pamięci.

Zliczanie odwołań można również zaimplementować, tak aby wszystkie odwołania do obiektu (nie do poszczególnych interfejsów) były zliczane. W tym przypadku każdy `AddRef` i `Release` Wywołaj delegatów do centralnej implementacji na obiekcie i `Release` zwolni cały obiekt, gdy jego licznik odwołań osiągnie wartość zero.

> [!NOTE]
> Gdy `CComObject` obiekt pochodny jest konstruowany przy użyciu **`new`** operatora, licznik odwołań jest równy 0. W związku z tym, wywołanie `AddRef` musi zostać wykonane po pomyślnym utworzeniu `CComObject` obiektu pochodnego.

## <a name="see-also"></a>Zobacz także

[Wprowadzenie do modelu COM](../atl/introduction-to-com.md)<br/>
[Zarządzanie okresami istnienia obiektów poprzez zliczanie odwołań](/windows/win32/com/managing-object-lifetimes-through-reference-counting)
