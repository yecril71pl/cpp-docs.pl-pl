---
title: Ustawianie właściwości klawiszy skrótów (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- accelerator properties
- properties [C++], accelerator properties
- Type property
- Key property
- Modifier property
- VIRTKEY
- Key property
- ID property
ms.assetid: 0fce9156-3025-4e18-b034-e219a4c65812
ms.openlocfilehash: e1fac31635b7ccc09f9c184cf734fa4f7717cb97
ms.sourcegitcommit: 5beace7dcc6bf0e8b8cc96a930e7424f9daa05cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2019
ms.locfileid: "55232139"
---
# <a name="setting-accelerator-properties"></a>Ustawianie właściwości klawiszy skrótów

Można ustawić właściwości klawiszy skrótów w [okno właściwości](/visualstudio/ide/reference/properties-window) w dowolnym momencie. Można również użyć [Edytor klawiszy skrótów](../windows/accelerator-editor.md) do modyfikowania właściwości klawiszy skrótów w tabeli klawiszy skrótu. Zmiany wprowadzone przy użyciu **właściwości** okna lub **akceleratora** Edytor ma ten sam wynik: zmiany są natychmiast odzwierciedlane w tabeli klawiszy skrótu.

## <a name="id-property"></a>ID — Właściwość

**Identyfikator** właściwości odwołuje się do każdego wpisu tabeli akceleratora w kodzie programu. Ten wpis jest wartość polecenia, który program otrzyma po naciśnięciu klawisza skrótu lub kombinację klawiszy. Aby akceleratora taki sam jak element menu, należy ich identyfikatorów takie same (tak długo, jak identyfikator tabeli klawiszy skrótu jest taki sam jak identyfikator zasobu menu).

Istnieją trzy właściwości dla każdego identyfikator akceleratora: **modyfikator** właściwości **klucz** właściwości i **typu** właściwości.

## <a name="modifier-property"></a>Modifier — Właściwość

**Modyfikator** właściwość ustawia kontroli kombinacje klawiszy dla akceleratora.

> [!NOTE]
> W **właściwości** okna, właściwość ta pojawia się jako trzy osobne **logiczna** właściwości, które mogą być kontrolowane niezależnie: **ALT**, **Ctrl**, i **Shift**.

Poniżej znajdują się wpisy prawne **modyfikator** właściwości w tabeli akceleratora:

   |Wartość|Opis|
   |-----------|-----------------|
   |**Brak**|Użytkownik naciśnie tylko **klucz** wartość. Ta wartość jest najbardziej efektywne używana przy użyciu wartości ASCII/ANSI 001 za pośrednictwem 026, który jest interpretowany jako ^ od A do ^ Z (**Ctrl + A** za pośrednictwem **Ctrl + Z**).|
   |**ALT**|Użytkownik musi nacisnąć klawisz **Alt** klucza przed **klucz** wartość.|
   |**Ctrl**|Użytkownik musi nacisnąć klawisz **Ctrl** klucza przed **klucz** wartość. Nie jest prawidłowy z typem ASCII.|
   |**SHIFT**|Użytkownik musi nacisnąć klawisz **Shift** klucza przed **klucz** wartość.|
   |**Ctrl+Alt**|Użytkownik musi nacisnąć klawisz **Ctrl** klucza i **Alt** klucza przed **klucz** wartość. Nie jest prawidłowy z typem ASCII.|
   |**Ctrl+Shift**|Użytkownik musi nacisnąć klawisz **Ctrl** klucza i **Shift** klucza przed **klucz** wartość. Nie jest prawidłowy z typem ASCII.|
   |**Alt+Shift**|Użytkownik musi nacisnąć klawisz **Alt** klucza i **Shift** klucza przed **klucz** wartość. Nie jest prawidłowy z typem ASCII.|
   |**Ctrl+Alt+Shift**|Użytkownik musi nacisnąć klawisz **Ctrl**, **Alt**, i **Shift** przed **klucz** wartość. Nie jest prawidłowy z typem ASCII.|

## <a name="key-property"></a>Key — Właściwość

**Klucz** właściwość ustawia rzeczywistego klucza do użycia jako akcelerator.

Poniżej znajdują się wpisy prawne **klucz** właściwości w tabeli akceleratora:

   |Wartość|Opis|
   |-----------|-----------------|
   |Liczba całkowita między 0 a 255 w formacie dziesiętnym.|Wartość określa, czy wartość jest traktowana jako ASCII i ANSI w następujący sposób:<br/><br/>-Cyfr są zawsze interpretowane jako odpowiadający mu klucz, a nie jako wartości ASCII lub ANSI.<br/>-Wartości z zakresu od 1 do 26, gdy poprzedzony zerami, są interpretowane jako ^ od A do ^ Z, która reprezentuje wartość ASCII litery alfabetu, po naciśnięciu z **Ctrl** przytrzymanie klawisza.<br/>-Wartościami z 27 32 są zawsze interpretowane jako wartości dziesiętne trzycyfrowy 027 za pośrednictwem 032.<br/>-Wartości z kolekcji 033 do 255, czy poprzedzony przez użytkownika 0 nie będą interpretowane jako wartości ANSI.|
   |Znak pojedynczego klawiatury.|Wielkie litery A - Z lub cyfry 0 - 9 mogą być ASCII lub wirtualny wartości klucza. jakikolwiek inny znak jest ASCII tylko.|
   |Klawiatury pojedynczy znak z zakresu A - Z (tylko wielkie litery), poprzedzony daszek (^) (na przykład ^ C).|Ta opcja wprowadza wartość ASCII klucza po naciśnięciu klawisza z **Ctrl** przytrzymanie klawisza.|
   |Wszystkie prawidłowe wirtualny identyfikator klawisza.|Pole listy rozwijanej klucza w tabeli akceleratora zawiera standardowe wirtualnych identyfikatorów klucza.|

> [!NOTE]
> Podczas wprowadzania wartości ASCII, opcje właściwości modyfikator są ograniczone. Jest tylko klawisz control dostępne do użytku **Alt** klucza.

> [!TIP]
> Innym sposobem zdefiniowania klawiszem skrótu jest kliknij prawym przyciskiem myszy wpis lub wiele wpisów w tabeli akceleratora, wybierz polecenie **dalej wpisany klucz** z menu skrótów, a następnie naciśnij klawisze lub kombinacji klawiszy na klawiaturze. **Dalej wpisany klucz** polecenia jest także dostępny z **Edytuj** menu.

## <a name="type-property"></a>Type — Właściwość

**Typu** właściwość określa, czy klawisz skrótu skojarzony identyfikator akceleratora, jest interpretowany jako wartość klucza ASCII/ANSI lub kombinacji klawisza wirtualnego (VIRTKEY).

- Jeśli **typu** właściwość jest ASCII, **modyfikator** właściwości mogą być tylko `None` lub `Alt`, lub może być akceleratora, który używa **Ctrl** klucza () określony przez poprzedzający klucza o `^`).

- Jeśli **typu** właściwość jest VIRTKEY i dowolną kombinację `Modifier` i `Key` wartości jest prawidłowy.

> [!NOTE]
> Jeśli chcesz wprowadzić wartość w tabeli akceleratora i wartości traktowane jak ASCII/ANSI, po prostu kliknij **typu** wpisu w tabeli i ASCII wybierz z listy rozwijanej. Jednak jeśli używasz **dalej wpisany klucz** polecenia (**Edytuj** menu) do określenia `Key`, należy zmienić **typu** właściwość VIRTKEY ASCII *przed* wprowadzania `Key` kodu.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Edytowanie w tabeli klawiszy skrótu](../windows/editing-in-an-accelerator-table.md)<br/>
[Wstępnie zdefiniowane klawisze skrótów](../windows/predefined-accelerator-keys.md)<br/>
[Edytory zasobów](../windows/resource-editors.md)<br/>
