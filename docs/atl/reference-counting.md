---
title: Zliczanie referencyjne (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- AddRef method [C++], reference counting
- reference counting
- AddRef method [C++]
- reference counts
- references, counting
ms.assetid: b1fd4514-6de6-429f-9e60-2777c0d07a3d
ms.openlocfilehash: 095f0ad2ecc1e1a870077899d61a3c594f8cc95f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321742"
---
# <a name="reference-counting"></a>Zliczanie odwołań

Sama com nie próbuje automatycznie usunąć obiekt z pamięci, gdy uważa, że obiekt nie jest już używany. Zamiast tego programator obiektu musi usunąć nieużyny obiekt. Programator określa, czy obiekt może zostać usunięty na podstawie liczby odwołań.

COM używa `IUnknown` metod [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) i [Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release), do zarządzania liczbą odwołań interfejsów na obiekcie. Ogólne zasady wywoływania tych metod to:

- Za każdym razem, gdy `AddRef` klient odbiera wskaźnik interfejsu, musi być wywoływana w interfejsie.

- Za każdym razem, gdy klient zakończył korzystanie `Release`ze wskaźnika interfejsu, musi wywołać .

W prostej implementacji każde `AddRef` wywołanie `Release` zwiększa się, a każde wywołanie zmniejsza zmienną licznika wewnątrz obiektu. Gdy liczba powróci do zera, interfejs nie ma już żadnych użytkowników i może usunąć się z pamięci.

Zliczanie odwołań można również zaimplementować tak, aby każde odwołanie do obiektu (nie do pojedynczego interfejsu) jest liczone. W takim przypadku `AddRef` `Release` każdy i wywołać delegatów do `Release` centralnej implementacji na obiekcie i zwalnia cały obiekt, gdy jego liczba odwołań osiągnie zero.

> [!NOTE]
> `CComObject`Gdy obiekt pochodny jest konstruowany przy użyciu **nowego** operatora, liczba odwołań wynosi 0. W związku z `AddRef` tym wywołanie musi być `CComObject`wykonane po pomyślnym utworzeniu obiektu pochodnego.

## <a name="see-also"></a>Zobacz też

[Wprowadzenie do modelu COM](../atl/introduction-to-com.md)<br/>
[Zarządzanie okresami istnienia obiektów za pomocą zliczania odwołań](/windows/win32/com/managing-object-lifetimes-through-reference-counting)
