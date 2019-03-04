---
title: Kreator okna dialogowego ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.dlg.overview
helpviewer_keywords:
- ATL projects, adding dialog resources
- ATL Dialog Wizard
ms.assetid: b0b9ace5-83c9-40d3-82c3-eb6293f10583
ms.openlocfilehash: 043c170021ce1ceb072dba3e5a450375f556753a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287924"
---
# <a name="atl-dialog-wizard"></a>Kreator okna dialogowego ATL

Ten kreator wstawia do projektu obiekt okno dialogowe ATL, pochodzące z [CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md). Okno dialogowe pochodną `CAxDialogImpl` może obsługiwać formantów ActiveX.

Kreator utworzy zasobu okna dialogowego z domyślną **OK** i **anulować** przycisków. Możesz edytować zasobu okna dialogowego i dodawanie kontrolek ActiveX przy użyciu [Edytor okien dialogowych](../../windows/dialog-editor.md) w widoku zasobów.

Kreator wstawia do pliku nagłówka [mapy komunikatów](../../atl/message-maps-atl.md) i deklaracji w zakresie obsługi domyślnie zdarzenia kliknięcia. Zobacz [Implementowanie okna dialogowego](../../atl/implementing-a-dialog-box.md) uzyskać więcej informacji dotyczących biblioteki ATL, okno dialogowe.

- **Krótka nazwa**

   Ustawia skróconą nazwę obiektu okna dialogowego ATL. Podana nazwa określa nazwę klasy i nazwy (.cpp i .h) plików, chyba że zmienił się tych pól indywidualnie.

- **Class**

   Ustawia nazwę klasy, która ma zostać utworzony. Ta nazwa jest na podstawie nazwy podane **krótką nazwę**, poprzedzającą "C", typowy prefiks dla nazwy klasy.

- **plik .h**

   Określa nazwę pliku nagłówkowego klasy nowego obiektu. Domyślnie ta nazwa jest na podstawie nazwy podane **krótką nazwę**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku na lokalizację lub dołączyć deklaracji klasy do istniejącego pliku. Jeśli wybierzesz istniejący plik, Kreator nie zapisze go w wybranej lokalizacji do momentu kliknij **Zakończ** w kreatorze.

   Kreator nie powoduje zastąpienia pliku. Jeśli wybierasz nazwę istniejącego pliku, po kliknięciu **Zakończ**, Kreator wyświetli monit o wskazują, czy deklaracja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** można dołączyć pliku kliknij przycisk **nie** aby powrócić do kreatora i podaj inną nazwę pliku.

- **Plik CPP**

   Określa nazwę pliku implementacji dla nowego obiektu klasy. Domyślnie ta nazwa jest na podstawie nazwy podane **krótką nazwę**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji. Plik nie jest zapisywany w wybranej lokalizacji, dopóki nie klikniesz **Zakończ** w kreatorze.

   Kreator nie powoduje zastąpienia pliku. Jeśli wybierasz nazwę istniejącego pliku, po kliknięciu **Zakończ**, Kreator wyświetli monit o wskazują, czy Implementacja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** można dołączyć pliku kliknij przycisk **nie** aby powrócić do kreatora i podaj inną nazwę pliku.

## <a name="see-also"></a>Zobacz także

[Okno dialogowe ATL](../../atl/reference/adding-an-atl-dialog-box.md)
