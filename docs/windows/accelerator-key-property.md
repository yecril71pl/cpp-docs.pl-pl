---
title: Właściwość klawisza skrótu (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Key property
ms.assetid: d1570cd9-b414-4cd6-96bd-47c38281eaca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e0594e5b9e2d092330664546cbd05ccfb0060c42
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428970"
---
# <a name="accelerator-key-property-c"></a>Właściwość klawisza skrótu (C++)

Dostępne są następujące wpisy prawne dla właściwości klucza w tabeli akceleratora:

- Liczba całkowita między 0 a 255 w formacie dziesiętnym. Wartość określa, czy wartość jest traktowana jako ASCII i ANSI w następujący sposób:

   - Cyfr są zawsze interpretowane jako odpowiadający mu klucz, a nie jako wartości ASCII lub ANSI.

   - Wartości z zakresu od 1 do 26, gdy poprzedzony zerami, są interpretowane jako ^ od A do ^ Z, która reprezentuje wartość ASCII litery alfabetu, po naciśnięciu z **Ctrl** przytrzymanie klawisza.

   - Wartości z 27 32 zawsze są interpretowane jako wartości dziesiętne trzycyfrowy 027 za pośrednictwem 032.

   - Wartości z 033 do 255, czy poprzedzony przez użytkownika 0 nie będą interpretowane jako wartości ANSI.

- Znak pojedynczego klawiatury. Wielkie litery A - Z lub cyfry 0 - 9 mogą być ASCII lub wirtualny wartości klucza. jakikolwiek inny znak jest ASCII tylko.

- Klawiatury pojedynczy znak z zakresu A - Z (tylko wielkie litery), poprzedzony daszek (^) (na przykład ^ C). Wprowadza wartość ASCII klucza, po naciśnięciu klawisza z **Ctrl** przytrzymanie klawisza.

   > [!NOTE]
   > Podczas wprowadzania wartości ASCII, opcje właściwości modyfikator są ograniczone. Jest tylko klawisz control dostępne do użytku **Alt** klucza.

- Wszystkie prawidłowe wirtualny identyfikator klawisza. Pole listy rozwijanej klucza w tabeli akceleratora zawiera standardowe wirtualnych identyfikatorów klucza.

   > [!TIP]
   > Innym sposobem zdefiniowania klawiszem skrótu jest kliknij prawym przyciskiem myszy wpis lub wiele wpisów w tabeli akceleratora, wybierz polecenie **dalej wpisany klucz** z menu skrótów, a następnie naciśnij klawisze lub kombinacji klawiszy na klawiaturze. **Dalej wpisany klucz** polecenia jest także dostępny z **Edytuj** menu.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Ustawianie właściwości klawiszy skrótów](../windows/setting-accelerator-properties.md)<br/>
[Edytowanie w tabeli klawiszy skrótu](../windows/editing-in-an-accelerator-table.md)<br/>
[Edytor klawiszy skrótów](../windows/accelerator-editor.md)